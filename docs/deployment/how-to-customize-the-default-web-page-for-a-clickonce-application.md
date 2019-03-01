---
title: 'Comment : personnaliser la Page Web par défaut pour une Application ClickOnce | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9831c1176b5e71650742226e77bfca58dfa35a01
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56608443"
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>Guide pratique pour personnaliser la page web par défaut d’une application ClickOnce
Lorsque vous publiez une application ClickOnce sur le Web, une page Web est automatiquement générée et publiée avec l’application. La page par défaut contient le nom de l’application et les liens pour installer l’application, installez les composants requis ou accéder à l’aide sur MSDN.

> [!NOTE]
>  Les liens réels que vous voyez sur la page dépendent de l’ordinateur où la page est affichée et ce que vous incluez de conditions préalables.

 Le nom par défaut pour la page Web est *Publish.htm*; vous pouvez modifier le nom dans la **Concepteur de projet**. Pour plus d’informations, consultez [Comment : spécifier une page de publication pour une application ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md).

 Le *Publish.htm* page Web est publiée uniquement si une version plus récente est détectée.

> [!NOTE]
>  Les modifications que vous apportez à votre **publier** paramètres n’affectent pas le *Publish.htm* page, à une exception près : Si vous ajoutez ou supprimez des composants requis après la publication initiale, la liste des composants requis sera ne plus être correctes. Vous devrez modifier le texte du lien Configuration requise refléter les modifications.

### <a name="to-customize-the-publish-web-page"></a>Pour personnaliser la page Web de publication

1.  Publiez votre application ClickOnce à un emplacement Web. Pour plus d’informations, consultez [Comment : publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

2.  Sur le serveur Web, ouvrez le *Publish.htm* fichier dans Visual Web Designer ou un autre éditeur HTML.

3.  Personnaliser la page comme vous le souhaitez et l’enregistrer.

4.  Optionnel. Pour empêcher Visual Studio de remplacer votre page Web de publication personnalisée, décochez la case **générer automatiquement la page Web de déploiement après chaque publication** dans le **Options de publication** boîte de dialogue.

## <a name="see-also"></a>Voir aussi
- [Sécurité et déploiement ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Publication d’applications ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Guide pratique pour installer les composants requis avec une application ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [Guide pratique pour spécifier une page de publication pour une application ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)