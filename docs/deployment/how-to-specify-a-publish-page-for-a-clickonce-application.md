---
title: 'Comment : spécifier une Page de publication pour une Application ClickOnce | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 864d0ef0f4934e040722a9a9fc00ba7a54f3331c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-specify-a-publish-page-for-a-clickonce-application"></a>Comment : spécifier une page de publication pour une application ClickOnce
Lorsque vous publiez un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application, une page Web de valeur par défaut (publish.htm) est générée et publiée avec l’application. Cette page contient le nom de l’application, un lien permettant d’installer l’application et/ou les composants requis et un lien vers une rubrique d’aide décrivant [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Le **Page Publish** propriété pour votre projet vous permet de spécifier un nom pour la page Web pour votre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application.  
  
 Une fois que la page de publication a été spécifiée, la prochaine fois que vous publiez, il sera copié à l’emplacement de publication ; Il ne sera pas remplacé si vous publiez à nouveau. Si vous souhaitez personnaliser l’apparence de la page, vous pouvez le faire sans vous préoccuper de perdre vos modifications. Pour plus d’informations, consultez [Comment : personnaliser la Page Web par défaut de ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md).  
  
 Le **publier une Page** propriété peut être définie le **Options de publication** boîte de dialogue, accessible à partir de la **publier** volet de la **le Concepteur de projets**.  
  
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
 [Comment : personnaliser la Page Web par défaut de ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)