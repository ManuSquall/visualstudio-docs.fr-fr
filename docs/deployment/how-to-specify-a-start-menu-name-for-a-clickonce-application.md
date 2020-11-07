---
title: Spécifier le nom du menu Démarrer pour une application ClickOnce
description: Découvrez comment modifier le nom d’affichage de votre application ClickOnce en définissant Product Name dans la boîte de dialogue Options de publication.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Start menu resource name
- Start menu name
- ClickOnce deployment, Start menu name
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12a6ebce0ff3bb7c3040765c1a82f876d0055c4d
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349670"
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>Guide pratique pour spécifier un nom de menu Démarrer pour une application ClickOnce
Lorsqu’une [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application est installée pour une utilisation en ligne et hors connexion, une entrée est ajoutée au menu **Démarrer** et à la liste **Ajouter ou supprimer des programmes** . Par défaut, le nom complet est le même que le nom de l’assembly d’application, mais vous pouvez modifier le nom complet en définissant le **nom du produit** dans la boîte de dialogue **options de publication** .

 Le **nom du produit** s’affiche sur la page *publish.htm* ; pour une application hors connexion installée, il s’agit du nom de l’entrée dans le menu **Démarrer** , et il s’agit également du nom qui s’affiche dans **Ajout/suppression de programmes**.

 **Le nom** de l’éditeur apparaît sur la page *publish.htm* au-dessus du **nom du produit** , et pour une application hors connexion installée, il s’agit également du nom du dossier qui contient l’icône de l’application dans le menu **Démarrer** .

 Le raccourci du menu Démarrer ou la référence de l’application est créé dans *\\<\> %AppData%\Microsoft\Windows\Start \ nom* de l’éditeur. La référence du raccourci ou de l’application porte le même nom que le nom du produit.

 Vous pouvez définir les **Propriétés nom du produit** et nom de l' **éditeur** dans la boîte de dialogue **options de publication** , disponible sur la page **publier** du concepteur de **projets**.

### <a name="to-specify-a-start-menu-name"></a>Pour spécifier un nom de menu Démarrer

1. Après avoir sélectionné un projet dans l’ **Explorateur de solutions** , dans le menu **Projet** , cliquez sur **Propriétés**.

2. Cliquez sur l'onglet **Publier**.

3. Cliquez sur le bouton **options** pour ouvrir la boîte de dialogue **options de publication** .

4. Cliquez sur **Description**.

5. Dans la boîte de dialogue **options de publication** , entrez le nom à afficher dans **nom du produit**.

6. Si vous le souhaitez, vous pouvez entrer un nom d’éditeur dans nom de l' **éditeur**.

## <a name="see-also"></a>Voir aussi
- [Publier des applications ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Comment : publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)