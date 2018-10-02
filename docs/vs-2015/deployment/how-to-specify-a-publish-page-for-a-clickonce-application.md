---
title: 'Comment : spécifier une Page de publication pour une Application ClickOnce | Microsoft Docs'
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
- deploying applications [ClickOnce], specifying publish page
- Publish Page property
- publishing, ClickOnce
- ClickOnce deployment, specifying publish page
ms.assetid: 9d70eebb-bdee-4b42-8e7e-7a07e199bdf7
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: c1aeb81c6430e8ee4719565dd52c7e404c860939
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504274"
---
# <a name="how-to-specify-a-publish-page-for-a-clickonce-application"></a>Comment : spécifier une page de publication pour une application ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : spécifier une Page de publication pour une Application ClickOnce](https://docs.microsoft.com/visualstudio/deployment/how-to-specify-a-publish-page-for-a-clickonce-application).  
  
Lorsque vous publiez un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application, une page de Web par défaut (publish.htm) est générée et publiée avec l’application. Cette page contient le nom de l’application, un lien pour installer l’application et/ou les composants requis et un lien vers une rubrique d’aide décrivant [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]. Le **Page Publier** propriété pour votre projet vous permet de spécifier un nom pour la page Web pour votre [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application.  
  
 Une fois que la page de publication a été spécifiée, la prochaine fois que vous publiez, il sera copié à l’emplacement de publication ; elle ne sera pas remplacée si vous publiez à nouveau. Si vous souhaitez personnaliser l’apparence de la page, vous pouvez le faire sans craindre de perdre vos modifications. Pour plus d’informations, consultez [Comment : personnaliser la Page Web par défaut de ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md).  
  
 Le **Page Publier** propriété peut être définie le **Options de publication** boîte de dialogue, accessible à partir de la **publier** volet de la **le Concepteur de projets**.  
  
### <a name="to-specify-a-custom-web-page-for-a-clickonce-application"></a>Pour spécifier une page Web personnalisée pour une application ClickOnce  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Sélectionnez le **publier** volet.  
  
3.  Cliquez sur le **Options** bouton pour ouvrir la **Options de publication** boîte de dialogue.  
  
4.  Cliquez sur **déploiement**.  
  
5.  Dans le **Options de publication** boîte de dialogue zone, assurez-vous que le **page web de déploiement ouverts après la publication** case à cocher est activée (elle doit être sélectionnée par défaut).  
  
6.  Dans le **page web de déploiement :** zone, entrez le nom de votre page Web, puis cliquez sur **OK**.  
  
### <a name="to-prevent-the-publish-page-from-launching-each-time-you-publish"></a>Pour empêcher le lancement de chaque fois que vous publiez la page de publication  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Sélectionnez le **publier** volet.  
  
3.  Cliquez sur le **Options** bouton pour ouvrir la **Options de publication** boîte de dialogue.  
  
4.  Cliquez sur **déploiement**.  
  
5.  Dans le **Options de publication** boîte de dialogue, désactivez le **page web de déploiement ouverts après la publication** case à cocher.  
  
## <a name="see-also"></a>Voir aussi  
 [Publication d’applications ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Guide pratique pour publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Guide pratique pour personnaliser la page web par défaut de ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)



