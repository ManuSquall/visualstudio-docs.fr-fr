---
title: L’accès est refusé | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 8a512060-d744-47af-a83e-4ba42ea2c5b2
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 9c097cd09712d19acf5a0e4999b5c7a47469f958
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24632729"
---
# <a name="access-is-denied"></a>Accès refusé
Un script a essayé d'accéder aux données à partir d'une source autre que l'hôte de la page actuelle. La stratégie d'origine suivie par Internet Explorer et d'autres navigateurs permet aux scripts d'accéder aux données uniquement à partir de sources avec les mêmes schéma, hôte et port de l'URL de la page actuelle.  
  
 Par exemple, si la page actuelle est https://employees.mycompany.com, vous ne pouvez pas accéder aux données à partir des URL suivantes :  
  
-   http://data.contoso.com, car elle utilise HTTP et non HTTPS.  
  
-   https://somedatasource.com, car il s'agit d'un autre domaine.  
  
-   https://employees.mycompany.com:8888, car elle utilise un port différent.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Vérifiez si l'API que vous essayez d'appeler prend en charge JSONP ou CORS, qui sont deux approches qui autorisent en toute sécurité les scripts cross-origin.  
  
-   Si vous essayez d'appeler une API REST, refactorisez cet appel vers votre code côté serveur, puis exposez un nouveau point de terminaison REST pour vos scripts côté client.  
  
     Pour plus d'informations, recherchez la documentation en ligne relative à la stratégie d'origine, JSONP et CORS.