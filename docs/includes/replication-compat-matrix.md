---
author: MashaMSFT
ms.service: sql
ms.topic: include
ms.date: 11/14/2018
ms.author: mathoma
ms.openlocfilehash: c4e33852ab323a23871668a9758d3f5bc0d724aa
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68212341"
---
### <a name="transactional-replication-matrix"></a>Matrix für die Transaktionsreplikation 

| **Verleger**   | **Verteiler** | **Abonnent** |
| :------------   | :-------------- | :------------- |
| SQL Server 2017 | SQL Server 2017 | SQL Server 2017 <br/> SQL Server 2016 <br/> SQLServer 2014 |
| SQL Server 2016 | SQL Server 2017 <br/> SQL Server 2016 | SQL Server 2017 <br/>SQL Server 2016 <br/> SQLServer 2014 <br/> SQL Server 2012 |
| SQLServer 2014 | SQL Server 2017 <br/> SQL Server 2016 <br/> SQLServer 2014 <br/>| SQL Server 2017 <br/> SQL Server 2016 <br/> SQLServer 2014 <br/> SQL Server 2012 <br/> SQL Server 2008 R2 <br/> SQL Server 2008 |
| SQL Server 2012 | SQL Server 2017 <br/> SQL Server 2016 <br/> SQLServer 2014 <br/>SQL Server 2012 <br/> | SQL Server 2016 <br/> SQLServer 2014 <br/> SQL Server 2012 <br/> SQL Server 2008 R2 <br/> SQL Server 2008 | 
| SQL Server 2008 R2 <br/> SQL Server 2008 | SQL Server 2017 <br/> SQL Server 2016 <br/> SQLServer 2014 <br/>SQL Server 2012 <br/> SQL Server 2008 R2 <br/> SQL Server 2008 | SQLServer 2014 <br/> SQL Server 2012 <br/> SQL Server 2008 R2 <br/> SQL Server 2008 <br/>  |
| &nbsp; | &nbsp; | &nbsp; |

### <a name="merge-replication-support-matrix"></a>Supportmatrix für die Mergereplikation
| **Verleger**   | **Verteiler** | **Abonnent** |
| :------------   | :-------------- | :------------- |
| SQL Server 2017 | SQL Server 2017 | SQL Server 2017 <br/> SQL Server 2016 <br/> SQLServer 2014 <br/>SQL Server 2012 <br/> SQL Server 2008 R2 <br/> SQL Server 2008 | SQL Server 2008 R2 <br/> SQL Server 2008  |
| SQL Server 2016 | SQL Server 2017 <br/> SQL Server 2016 | SQL Server 2016 <br/> SQLServer 2014 <br/>SQL Server 2012 <br/> SQL Server 2008 R2 <br/> SQL Server 2008 | SQL Server 2008 R2 <br/> SQL Server 2008  |
| SQLServer 2014 | SQL Server 2017 <br/> SQL Server 2016 <br/> SQLServer 2014 <br/>| SQLServer 2014 <br/>SQL Server 2012 <br/> SQL Server 2008 R2 <br/> SQL Server 2008 | SQL Server 2008 R2 <br/> SQL Server 2008  |
| SQL Server 2012 | SQL Server 2017 <br/> SQL Server 2016 <br/> SQLServer 2014 <br/>SQL Server 2012 <br/> | SQL Server 2012 <br/> SQL Server 2008 R2 <br/> SQL Server 2008 | 
| SQL Server 2008 R2 <br/> SQL Server 2008 | SQL Server 2017 <br/> SQL Server 2016 <br/> SQLServer 2014 <br/>SQL Server 2012 <br/> SQL Server 2008 R2 <br/> SQL Server 2008 | SQL Server 2008 R2 <br/> SQL Server 2008  |
| &nbsp; | &nbsp; | &nbsp; |