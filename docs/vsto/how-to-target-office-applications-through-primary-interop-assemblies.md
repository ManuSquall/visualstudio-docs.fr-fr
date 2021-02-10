---
title: Cibler des applications Office par le biais d’assemblys PIA
description: Découvrez comment vous pouvez utiliser Visual Studio pour cibler par programmation Microsoft Office applications par le biais d’assemblys PIA (Primary Interop Assembly).
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- assemblies [Office development in Visual Studio], PIA references
- primary interop assemblies [Office development in Visual Studio], adding references to
- Office primary interop assemblies in Visual Studio, adding references to
- Office applications [Office development in Visual Studio], automating
- application development [Office development in Visual Studio], automating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 11a0db0e23cf5512a6568ba5b66e0c18e563bd12
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962377"
---
# <a name="how-to-target-office-applications-through-primary-interop-assemblies"></a>Comment : cibler des applications Office par le biais d’assemblys PIA
  Quand vous créez un projet Office, Visual Studio ajoute automatiquement des références aux assemblys PIA (Primary Interop Assembly) Microsoft Office qui sont requises pour générer le projet Vous devez ajouter des références aux autres assemblys PIA dans les scénarios suivants :

- Vous souhaitez utiliser des fonctionnalités d'autres applications Microsoft Office dans votre projet. Par exemple, vous pouvez utiliser des fonctionnalités de Microsoft Office Excel dans un projet pour Microsoft Office Word.

- Vous souhaitez automatiser des applications Microsoft Office qui n'ont pas de projets dédiés dans Visual Studio, comme Microsoft Office Access.

  [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="to-add-a-reference-to-a-primary-interop-assembly"></a>Pour ajouter une référence à un assembly PIA

1. Ouvrez votre projet Office et sélectionnez le nom du projet dans **Explorateur de solutions**.

2. Dans le menu **Projet**, cliquez sur **Ajouter une référence**.

3. Sous l’onglet **Framework** , sélectionnez l’assembly PIA de votre choix dans la liste **nom du composant** . Pour plus d’informations sur les assemblys PIA (Primary Interop Assembly) Microsoft Office disponibles, consultez Assemblys PIA ( [Primary Interop Assembly) Office](../vsto/office-primary-interop-assemblies.md).

     Si le projet cible le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure, la propriété **incorporer les types d’interopérabilité** pour la référence d’assembly a la valeur **true** par défaut. Grâce à ce paramètre, votre solution ne requiert pas l'assembly PIA sur les ordinateurs des utilisateurs finaux. Pour plus d’informations, consultez [conception et création de solutions Office](../vsto/designing-and-creating-office-solutions.md).

    > [!NOTE]
    > Dans les projets Office, ajoutez toujours des références aux assemblys PIA Office en utilisant l’onglet **.net** de la boîte de dialogue **Ajouter une référence** plutôt que l’onglet **com** . Pour plus d’informations, consultez [assemblys PIA (Primary Interop Assembly) Office](../vsto/office-primary-interop-assemblies.md).

4. Cliquez sur **OK**.

     Le nom de l’assembly apparaît dans le dossier **références** de **Explorateur de solutions**.

## <a name="see-also"></a>Voir aussi
- [Assemblys PIA (Primary Interop Assembly) Office](../vsto/office-primary-interop-assemblies.md)
- [Écrire du code dans les solutions Office](../vsto/writing-code-in-office-solutions.md)
- [Développer des solutions Office](../vsto/developing-office-solutions.md)
- [Comment : installer les assemblys PIA (Primary Interop Assembly) Office](../vsto/how-to-install-office-primary-interop-assemblies.md)
