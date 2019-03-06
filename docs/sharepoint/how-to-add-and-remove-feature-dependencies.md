---
title: 'Procédure : Ajouter et supprimer des dépendances de fonctionnalité | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- MICROSOFT.VISUALSTUDIO.SHAREPOINT.DESIGNERS.CUSTOMDEPENDENCYWINDOW
- VS.SHAREPOINTTOOLS.RAD.FEATUREDESIGNERDEPENDENCY
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 13fc731dcf5d96db569a969244b2375939afee62
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56636968"
---
# <a name="how-to-add-and-remove-feature-dependencies"></a>Procédure : Ajouter et supprimer des dépendances de fonctionnalité
  Votre fonctionnalité SharePoint peut dépendre d’autres fonctionnalités pour les fonctionnalités ou données. Dans ce cas, vous pouvez marquer ces fonctionnalités en tant que dépendances de votre fonction. De cette façon, le serveur SharePoint permet de s’assurer que les fonctionnalités dépendantes sont activées avant votre fonctionnalité est activée.

## <a name="add-dependencies"></a>Ajouter des dépendances
 Vous pouvez ajouter d’autres fonctionnalités dans votre solution en tant que dépendances. De cette façon, vous pouvez vous assurer que les fonctionnalités requises sont installées et activées avant que votre composant est installé.

#### <a name="to-add-a-dependency-on-a-feature-in-the-solution"></a>Pour ajouter une dépendance sur une fonctionnalité dans la solution

1.  Ouvrez le Concepteur de fonctionnalités, développez le **dépendances d’Activation de fonctionnalité** nœud, puis choisissez le **ajouter** bouton.

2.  Dans le **ajouter des dépendances d’Activation de fonctionnalité** boîte de dialogue, sélectionnez le **ajouter une dépendance sur les fonctionnalités de la solution** case d’option, cliquez sur le titre de la fonctionnalité que vous souhaitez ajouter en tant que dépendance, puis Choisissez le **ajouter** bouton.

     Vous pouvez ajouter plusieurs fonctionnalités en choisissant plusieurs titres lors du choix du **Ctrl** clé.

## <a name="addi-custom-dependencies"></a>Dépendances personnalisées Addi
 Vous pouvez ajouter des fonctionnalités qui sont déjà déployées sur un serveur SharePoint en tant que dépendance. De cette façon, le processus d’activation de SharePoint vérifie pour vous assurer que tous les composants dépendants sont activés avant que votre composant est installé.

#### <a name="to-add-a-dependency-by-the-feature-id"></a>Pour ajouter une dépendance par l’ID de fonctionnalité

1.  Ouvrez le Concepteur de fonctionnalités, développez le **dépendances d’Activation de fonctionnalité** nœud, puis choisissez le **ajouter** bouton.

2.  Dans le **ajouter des dépendances d’Activation de fonctionnalité** boîte de dialogue, sélectionnez le **ajouter une dépendance personnalisée** case d’option.

3.  Dans le **ID de la fonctionnalité** texte, entrez le GUID de la fonctionnalité que vous souhaitez marquer comme une dépendance d’activation, puis choisissez le **ajouter** bouton.

## <a name="edit-custom-dependencies"></a>Modifier des dépendances personnalisées
 Vous pouvez modifier des dépendances personnalisées que vous avez ajouté précédemment. Toutefois, les fonctionnalités qui sont dans votre solution peut uniquement être supprimé, pas modifiée.

#### <a name="to-change-a-dependency-on-a-feature-in-the-solution"></a>Pour modifier une dépendance sur une fonctionnalité dans la solution

1.  Ouvrez le Concepteur de fonctionnalités et développez le **dépendances d’Activation de fonctionnalité** nœud.

2.  Choisissez le nom de la fonctionnalité que vous souhaitez modifier, puis choisissez le **modifier** bouton.

3.  Dans le **modifier la dépendance d’Activation personnalisée fonctionnalité** boîte de dialogue Modifier le titre, un ID de fonctionnalité ou une description, puis choisissez le **envoyer** bouton.

## <a name="remove-dependencies"></a>Supprimer les dépendances

#### <a name="to-remove-a-dependency-on-a-feature-in-the-solution"></a>Pour supprimer une dépendance sur une fonctionnalité dans la solution

1.  Dans le Concepteur de fonctionnalités, développez le **dépendances d’Activation de fonctionnalité** nœud, choisissez le nom de la fonctionnalité que vous souhaitez supprimer, puis choisissez le **supprimer** bouton.

## <a name="see-also"></a>Voir aussi
- [Créer des fonctionnalités de SharePoint](../sharepoint/creating-sharepoint-features.md)
- [Guide pratique pour Personnaliser une fonctionnalité SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Guide pratique pour Ajouter et supprimer des éléments dans des fonctionnalités SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
