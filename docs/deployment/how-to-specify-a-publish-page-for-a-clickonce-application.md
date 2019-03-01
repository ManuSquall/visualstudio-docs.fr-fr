---
title: 'Comment : spécifier une Page de publication pour une Application ClickOnce | Microsoft Docs'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12a7d9dd2ad9d329fda5f27e78e24b0aa07cc3a6
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56598919"
---
# <a name="how-to-specify-a-publish-page-for-a-clickonce-application"></a>Guide pratique pour spécifier une page de publication pour une application ClickOnce
Lorsque vous publiez un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application, une page de Web par défaut (publish.htm) est générée et publiée avec l’application. Cette page contient le nom de l’application, un lien pour installer l’application et/ou les composants requis et un lien vers une rubrique d’aide décrivant [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Le **Page Publier** propriété pour votre projet vous permet de spécifier un nom pour la page Web pour votre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application.

 Une fois que la page de publication a été spécifiée, la prochaine fois que vous publiez, il sera copié à l’emplacement de publication ; elle ne sera pas remplacée si vous publiez à nouveau. Si vous souhaitez personnaliser l’apparence de la page, vous pouvez le faire sans craindre de perdre vos modifications. Pour plus d’informations, consultez [Comment : personnaliser la page Web par défaut ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md).

 Le **Page Publier** propriété peut être définie le **Options de publication** boîte de dialogue, accessible à partir de la **publier** volet de la **le Concepteur de projets**.

### <a name="to-specify-a-custom-web-page-for-a-clickonce-application"></a>Pour spécifier une page Web personnalisée pour une application ClickOnce

1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.

2.  Sélectionnez le **publier** volet.

3.  Cliquez sur le **Options** bouton pour ouvrir la **Options de publication** boîte de dialogue.

4.  Cliquez sur **déploiement**.

5.  Dans le **Options de publication** boîte de dialogue zone, assurez-vous que le **page web de déploiement ouverts après la publication** case à cocher est activée (elle doit être sélectionnée par défaut).

6.  Dans le **page web de déploiement** zone, entrez le nom de votre page Web, puis cliquez sur **OK**.

### <a name="to-prevent-the-publish-page-from-launching-each-time-you-publish"></a>Pour empêcher le lancement de chaque fois que vous publiez la page de publication

1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.

2.  Sélectionnez le **publier** volet.

3.  Cliquez sur le **Options** bouton pour ouvrir la **Options de publication** boîte de dialogue.

4.  Cliquez sur **déploiement**.

5.  Dans le **Options de publication** boîte de dialogue, désactivez le **page web de déploiement ouverts après la publication** case à cocher.

## <a name="see-also"></a>Voir aussi
- [Publier des applications ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Guide pratique pour publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [Guide pratique pour personnaliser la page web par défaut de ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)