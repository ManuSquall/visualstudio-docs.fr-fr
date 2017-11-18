---
title: "Comment : personnaliser la Page Web par défaut pour une Application ClickOnce | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish.htm Web page
- ClickOnce deployment default Web page
- deploying applications [ClickOnce], publishing
- publishing, ClickOnce
ms.assetid: 418de18c-bee9-4f24-9cd9-0252d175070d
caps.latest.revision: "14"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: fefafa0f9ea04a62d6ae79bd18834e36a1480f29
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>Comment : personnaliser la page Web par défaut d’une application ClickOnce
Lorsque vous publiez une application ClickOnce sur le Web, une page Web est automatiquement générée et publiée avec l’application. La page par défaut contient le nom de l’application et les liens pour installer l’application, installez les composants requis ou accéder à l’aide sur MSDN.  
  
> [!NOTE]
>  Les liens réels que vous voyez sur la page dépendent de l’ordinateur sur lequel la page est affichée et que vous incluez de conditions préalables.  
  
 Le nom par défaut pour la page Web est Publish.htm ; Vous pouvez modifier le nom dans la **Concepteur de projet**. Pour plus d’informations, consultez [Comment : spécifier une Page de publication pour une Application ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md).  
  
 La page Publish.htm Web est publiée uniquement si une version plus récente est détectée.  
  
> [!NOTE]
>  Les modifications que vous apportez à votre **publier** paramètres n’affectent pas la page Publish.htm, à une exception près : Si vous ajoutez ou supprimez des composants requis après la publication initiale, la liste des conditions préalables requises ne seront plus précise. Vous devez modifier le texte du lien requis refléter les modifications.  
  
### <a name="to-customize-the-publish-web-page"></a>Pour personnaliser la page Web de publication  
  
1.  Publier votre application ClickOnce à un emplacement Web. Pour plus d’informations, consultez [Comment : publier une Application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
2.  Sur le serveur Web, ouvrez le fichier Publish.htm dans le Concepteur Web visuel ou un autre éditeur HTML.  
  
3.  Personnaliser la page comme vous le souhaitez et l’enregistrer.  
  
4.  Facultatif. Pour empêcher Visual Studio de remplacer votre page Web de publication personnalisée, décochez la case **générer automatiquement la page web de déploiement après chaque publication** dans la boîte de dialogue Options de publication.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité et déploiement ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Publication d’applications ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Comment : installer les composants requis avec une Application ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Guide pratique pour spécifier une page de publication pour une application ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)