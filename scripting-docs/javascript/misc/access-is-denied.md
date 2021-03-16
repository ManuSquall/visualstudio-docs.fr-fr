---
description: Un script a essayé d'accéder aux données à partir d'une source autre que l'hôte de la page actuelle.
title: Accès refusé | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 8a512060-d744-47af-a83e-4ba42ea2c5b2
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 6be3bce0643a5892973235871191766cac140962
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571933"
---
# <a name="access-is-denied"></a>l’accès est refusé.
Un script a essayé d'accéder aux données à partir d'une source autre que l'hôte de la page actuelle. La stratégie d'origine suivie par Internet Explorer et d'autres navigateurs permet aux scripts d'accéder aux données uniquement à partir de sources avec les mêmes schéma, hôte et port de l'URL de la page actuelle.  
  
 Par exemple, si la page actuelle est `https://employees.mycompany.com` , vous ne pouvez pas accéder aux données à partir des URL suivantes :  
  
- `http://data.contoso.com`, car il utilise HTTP au lieu de HTTPs.  
  
- `https://somedatasource.com`, car il s’agit d’un domaine différent.  
  
- `https://employees.mycompany.com:8888`, car il utilise un autre port.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Vérifiez si l'API que vous essayez d'appeler prend en charge JSONP ou CORS, qui sont deux approches qui autorisent en toute sécurité les scripts cross-origin.  
  
- Si vous essayez d'appeler une API REST, refactorisez cet appel vers votre code côté serveur, puis exposez un nouveau point de terminaison REST pour vos scripts côté client.  
  
     Pour plus d'informations, recherchez la documentation en ligne relative à la stratégie d'origine, JSONP et CORS.
