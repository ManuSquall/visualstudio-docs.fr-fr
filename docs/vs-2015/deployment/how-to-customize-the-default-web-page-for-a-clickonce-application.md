---
title: 'Comment : personnaliser la Page Web par défaut pour une Application ClickOnce | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
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
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: bae699d0425f622f81ca14427934271b8d45eefb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47502361"
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>Comment : personnaliser la page Web par défaut d’une application ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : personnaliser la Page Web par défaut pour une Application ClickOnce](https://docs.microsoft.com/visualstudio/deployment/how-to-customize-the-default-web-page-for-a-clickonce-application).  
  
Lorsque vous publiez une application ClickOnce sur le Web, une page Web est automatiquement générée et publiée avec l’application. La page par défaut contient le nom de l’application et les liens pour installer l’application, installez les composants requis ou accéder à l’aide sur MSDN.  
  
> [!NOTE]
>  Les liens réels que vous voyez sur la page dépendent de l’ordinateur où la page est affichée et ce que vous incluez de conditions préalables.  
  
 Le nom par défaut pour la page Web est Publish.htm ; Vous pouvez modifier le nom dans la **Concepteur de projet**. Pour plus d’informations, consultez [Comment : spécifier une Page de publication pour une Application ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md).  
  
 La page Publish.htm Web est publiée uniquement si une version plus récente est détectée.  
  
> [!NOTE]
>  Les modifications que vous apportez à votre **publier** paramètres n’affectent pas la page Publish.htm, à une exception près : Si vous ajoutez ou supprimez des composants requis après la publication initiale, la liste des composants requis ne sera plus précise. Vous devrez modifier le texte du lien Configuration requise refléter les modifications.  
  
### <a name="to-customize-the-publish-web-page"></a>Pour personnaliser la page Web de publication  
  
1.  Publiez votre application ClickOnce à un emplacement Web. Pour plus d’informations, consultez [Comment : publier une Application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
2.  Sur le serveur Web, ouvrez le fichier Publish.htm dans Visual Web Designer ou un autre éditeur HTML.  
  
3.  Personnaliser la page comme vous le souhaitez et l’enregistrer.  
  
4.  Facultatif. Pour empêcher Visual Studio de remplacer votre page Web de publication personnalisée, décochez la case **générer automatiquement la page web de déploiement après chaque publication** dans la boîte de dialogue Options de publication.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité et déploiement ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Publication d’applications ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Guide pratique pour installer des composants requis avec une application ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Guide pratique pour spécifier une page de publication pour une application ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)



