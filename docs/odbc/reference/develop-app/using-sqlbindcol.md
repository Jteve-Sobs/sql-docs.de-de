---
title: Verwenden von SQLBindCol | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], binding columns
- binding columns [ODBC]
- SQLBindCol function [ODBC], using
ms.assetid: 17277ab3-33ad-44d3-a81c-a26b5e338512
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0f466d98d5d1edec2efa824ac644ad6bb49e990a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68022163"
---
# <a name="using-sqlbindcol"></a>Verwenden von SQLBindCol
Die Anwendung bindet Spalten durch den Aufruf **SQLBindCol**. Diese Funktion wird eine Spalte zu einem Zeitpunkt gebunden. Es gibt die Anwendung Folgendes an:  
  
-   Die Spaltennummer. Spalte 0 ist die Lesezeichenspalte. Diese Spalte ist in einigen Resultsets nicht enthalten. Alle anderen Spalten werden beginnend mit der Zahl 1 nummeriert. Es ist ein Fehler auf eine höhere-Spalte binden, als Spalten im Resultset vorhanden sind. Dieser Fehler nicht erkannt werden, bis das Resultset erstellt wurde, damit sie von zurückgegeben wird **SQLFetch**, nicht **SQLBindCol**.  
  
-   Die C-Daten Typ, Adresse und Byte der Länge der Variablen, die an die Spalte gebunden werden. Es ist ein Fehler an einen C-Datentyp, in dem der SQL-Datentyp der Spalte konvertiert werden kann. Dieser Fehler möglicherweise nicht erkannt werden, bis das Resultset erstellt wurde, damit sie von zurückgegeben wird **SQLFetch**, nicht **SQLBindCol**. Eine Liste der unterstützten Konvertierungen, finden Sie unter [Konvertieren von Daten aus SQL in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md) in Anhang D: Datentypen. Informationen über die Länge in Byte, finden Sie unter [Datenpufferlänge](../../../odbc/reference/develop-app/data-buffer-length.md).  
  
-   Die Adresse des ein Längen-/Indikatorpuffer. Die Längen-/Indikatorpuffer ist optional. Es wird verwendet, um die Bytelänge der Binär- oder Zeichendaten oder return SQL_NULL_DATA zurückzugeben, wenn die Daten NULL sind. Weitere Informationen finden Sie unter [mit Längenindikator/Werten](../../../odbc/reference/develop-app/using-length-and-indicator-values.md).  
  
 Wenn **SQLBindCol** wird aufgerufen, der Treiber ordnet diese Informationen mit der Anweisung. Wenn jede Datenzeile abgerufen wird, verwendet er die Informationen, um die Daten für jede Spalte in die gebundenen Anwendungsvariablen.  
  
 Der folgende Code bindet beispielsweise Variablen, den Verkäufer und CustID-Spalten. Daten für die Spalten zurückgegeben werden, *Vertriebsmitarbeiter* und *CustID*. Da *Vertriebsmitarbeiter* ein Puffer aus Zeichen, ist die Anwendung gibt die Bytelänge (11), sodass der Treiber zum Abschneiden der das bestimmen, ob kann. Die Bytelänge der zurückgegebenen des Titels oder, ob es NULL ist, werden im zurückgegeben *SalesPersonLenOrInd*.  
  
 Da *CustID* eine ganzzahlige Variable und hat den fester Länge, besteht keine Notwendigkeit, an die Bytelänge; der Treiber geht davon aus, es ist **Sizeof (** SQLUINTEGER **)** . Die Bytelänge der zurückgegebenen Kunden Daten-ID oder, ob es NULL ist, werden im zurückgegeben *CustIDInd*. Beachten Sie, dass nur in der gibt an, ob das Gehalt NULL ist, wird die Anwendung interessiert ist, da die Bytelänge immer **Sizeof (** SQLUINTEGER **)** .  
  
```  
SQLCHAR       SalesPerson[11];  
SQLUINTEGER   CustID;  
SQLINTEGER    SalesPersonLenOrInd, CustIDInd;  
SQLRETURN     rc;  
SQLHSTMT      hstmt;  
  
// Bind SalesPerson to the SalesPerson column and CustID to the   
// CustID column.  
SQLBindCol(hstmt, 1, SQL_C_CHAR, SalesPerson, sizeof(SalesPerson),  
            &SalesPersonLenOrInd);  
SQLBindCol(hstmt, 2, SQL_C_ULONG, &CustID, 0, &CustIDInd);  
  
// Execute a statement to get the sales person/customer of all orders.  
SQLExecDirect(hstmt, "SELECT SalesPerson, CustID FROM Orders ORDER BY SalesPerson",  
               SQL_NTS);  
  
// Fetch and print the data. Print "NULL" if the data is NULL. Code to   
// check if rc equals SQL_ERROR or SQL_SUCCESS_WITH_INFO not shown.  
while ((rc = SQLFetch(hstmt)) != SQL_NO_DATA) {  
   if (SalesPersonLenOrInd == SQL_NULL_DATA)   
            printf("NULL                     ");  
   else   
            printf("%10s   ", SalesPerson);  
   if (CustIDInd == SQL_NULL_DATA)   
         printf("NULL\n");  
   else   
            printf("%d\n", CustID);  
}  
  
// Close the cursor.  
SQLCloseCursor(hstmt);  
```  
  
 Der folgende Code führt eine **wählen** -Anweisung vom Benutzer eingegeben wurde, und gibt jede Zeile der Daten im Resultset. Da die Anwendung die Form der das Ergebnis nicht vorhersehbar ist, Festlegen von erstellt die **wählen** -Anweisung kann nicht bindet, bindet es hart kodierte Variablen auf das Ergebnis wie im vorhergehenden Beispiel festlegen. Stattdessen ordnet die Anwendung einen Puffer, der die Daten enthält und ein Längen-/Indikatorpuffer für jede Spalte in dieser Zeile. Für jede Spalte wird den Offset auf den Anfang des Speichers für die Spalte berechnet und diesen Offset so angepasst, dass die Daten und Längenindikator/Puffer für die Spalte auf Ausrichtungsgrenzen zu starten. Anschließend wird den Arbeitsspeicher, ab dem Offset der Spalte gebunden. Aus Sicht des Treibers ist die Adresse dieser Arbeitsspeicher von der Adresse einer Variablen, die im vorherigen Beispiel gebunden. Weitere Informationen zur Ausrichtung finden Sie unter [Ausrichtung](../../../odbc/reference/develop-app/alignment.md).  
  
```  
// This application allocates a buffer at run time. For each column, this   
// buffer contains memory for the column's data and length/indicator.   
// For example:  
//      column 1         column 2      column 3      column 4  
// <------------><---------------><-----><------------>  
//      db1   li1   db2   li2   db3   li3   db4   li4  
//      |      |      |      |      |      |      |         |  
//      _____V_____V________V_______V___V___V______V_____V_  
// |__________|__|_____________|__|___|__|__________|__|  
//  
// dbn = data buffer for column n  
// lin = length/indicator buffer for column n  
  
// Define a macro to increase the size of a buffer so that it is a   
// multiple of the alignment size. Thus, if a buffer starts on an   
// alignment boundary, it will end just before the next alignment   
// boundary. In this example, an alignment size of 4 is used because   
// this is the size of the largest data type used in the application's   
// buffer--the size of an SDWORD and of the largest default C data type   
// are both 4. If a larger data type (such as _int64) was used, it would   
// be necessary to align for that size.  
#define ALIGNSIZE 4  
#define ALIGNBUF(Length) Length % ALIGNSIZE ? \  
                  Length + ALIGNSIZE - (Length % ALIGNSIZE) : Length  
  
SQLCHAR        SelectStmt[100];  
SQLSMALLINT    NumCols, *CTypeArray, i;  
SQLINTEGER *   ColLenArray, *OffsetArray, SQLType, *DataPtr;  
SQLRETURN      rc;   
SQLHSTMT       hstmt;  
  
// Get a SELECT statement from the user and execute it.  
GetSelectStmt(SelectStmt, 100);  
SQLExecDirect(hstmt, SelectStmt, SQL_NTS);  
  
// Determine the number of result set columns. Allocate arrays to hold   
// the C type, byte length, and buffer offset to the data.  
SQLNumResultCols(hstmt, &NumCols);  
CTypeArray = (SQLSMALLINT *) malloc(NumCols * sizeof(SQLSMALLINT));  
ColLenArray = (SQLINTEGER *) malloc(NumCols * sizeof(SQLINTEGER));  
OffsetArray = (SQLINTEGER *) malloc(NumCols * sizeof(SQLINTEGER));  
  
OffsetArray[0] = 0;  
for (i = 0; i < NumCols; i++) {  
   // Determine the column's SQL type. GetDefaultCType contains a switch   
   // statement that returns the default C type for each SQL type.  
   SQLColAttribute(hstmt, ((SQLUSMALLINT) i) + 1, SQL_DESC_TYPE, NULL, 0, NULL, (SQLPOINTER) &SQLType);  
   CTypeArray[i] = GetDefaultCType(SQLType);  
  
   // Determine the column's byte length. Calculate the offset in the   
   // buffer to the data as the offset to the previous column, plus the   
   // byte length of the previous column, plus the byte length of the   
   // previous column's length/indicator buffer. Note that the byte   
   // length of the column and the length/indicator buffer are increased   
   // so that, assuming they start on an alignment boundary, they will  
   // end on the byte before the next alignment boundary. Although this   
   // might leave some holes in the buffer, it is a relatively   
   // inexpensive way to guarantee alignment.  
   SQLColAttribute(hstmt, ((SQLUSMALLINT) i)+1, SQL_DESC_OCTET_LENGTH, NULL, 0, NULL, &ColLenArray[i]);  
   ColLenArray[i] = ALIGNBUF(ColLenArray[i]);  
   if (i)  
      OffsetArray[i] = OffsetArray[i-1]+ColLenArray[i-1]+ALIGNBUF(sizeof(SQLINTEGER));  
}  
  
// Allocate the data buffer. The size of the buffer is equal to the   
// offset to the data buffer for the final column, plus the byte length   
// of the data buffer and length/indicator buffer for the last column.  
void *DataPtr = malloc(OffsetArray[NumCols - 1] +  
               ColLenArray[NumCols - 1] + ALIGNBUF(sizeof(SQLINTEGER)));  
  
// For each column, bind the address in the buffer at the start of the   
// memory allocated for that column's data and the address at the start   
// of the memory allocated for that column's length/indicator buffer.  
for (i = 0; i < NumCols; i++)  
   SQLBindCol(hstmt,  
            ((SQLUSMALLINT) i) + 1,  
            CTypeArray[i],  
            (SQLPOINTER)((SQLCHAR *)DataPtr + OffsetArray[i]),  
            ColLenArray[i],  
            (SQLINTEGER *)((SQLCHAR *)DataPtr + OffsetArray[i] + ColLenArray[i]));  
  
// Retrieve and print each row. PrintData accepts a pointer to the data,   
// its C type, and its byte length/indicator. It contains a switch   
// statement that casts and prints the data according to its type. Code   
// to check if rc equals SQL_ERROR or SQL_SUCCESS_WITH_INFO not shown.  
while ((rc = SQLFetch(hstmt)) != SQL_NO_DATA) {  
   for (i = 0; i < NumCols; i++) {  
      PrintData((SQLCHAR *)DataPtr[OffsetArray[i]], CTypeArray[i],  
               (SQLINTEGER *)((SQLCHAR *)DataPtr[OffsetArray[i] + ColLenArray[i]]));  
   }  
}  
  
// Close the cursor.  
SQLCloseCursor(hstmt);  
```
