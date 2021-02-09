---
title: Personnaliser la page Web par défaut pour l’application ClickOnce
description: En savoir plus sur la page Web générée lorsque vous publiez une application ClickOnce sur le Web, qui contient le nom de l’application et d’autres informations.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0377bdc5fa38c814bb5cd6ff02d12dcec117266d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900781"
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>Guide pratique pour personnaliser la page web par défaut d’une application ClickOnce
Lors de la publication d’une application ClickOnce sur le Web, une page Web est automatiquement générée et publiée avec l’application. La page par défaut contient le nom de l’application et des liens pour installer l’application, installer les composants requis ou accéder à l’aide sur MSDN.

> [!NOTE]
> Les liens réels que vous voyez sur la page dépendent de l’ordinateur sur lequel la page est affichée et des conditions préalables que vous incluez.

 Le nom par défaut de la page Web est *Publish.htm*; vous pouvez modifier le nom dans le **Concepteur de projet**. Pour plus d’informations, consultez [Comment : spécifier une page de publication pour une application ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md).

 La page Web *Publish.htm* est publiée uniquement si une version plus récente est détectée.

> [!NOTE]
> Les modifications que vous apportez à vos paramètres de **publication** n’affectent pas la page *Publish.htm* , à une exception près : Si vous ajoutez ou supprimez des composants requis après la publication initiale, la liste des composants requis ne sera plus exacte. Vous devrez modifier le texte du lien requis pour refléter les modifications.

### <a name="to-customize-the-publish-web-page"></a>Pour personnaliser la page Web de publication

1. Publiez votre application ClickOnce sur un emplacement Web. Pour plus d’informations, consultez [Comment : publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

2. Sur le serveur Web, ouvrez le fichier *Publish.htm* dans le concepteur Web visuel ou dans un autre éditeur HTML.

3. Personnalisez la page comme vous le souhaitez et enregistrez-la.

4. Facultatif. Pour empêcher Visual Studio de remplacer votre page Web de publication personnalisée, désactivez la case à cocher **générer automatiquement la page Web de déploiement après chaque publication** dans la boîte de dialogue **options de publication** .

## <a name="see-also"></a>Voir aussi
- [Sécurité et déploiement ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Publication d’applications ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Guide pratique pour installer les composants requis avec une application ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [Guide pratique pour spécifier une page de publication pour une application ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)