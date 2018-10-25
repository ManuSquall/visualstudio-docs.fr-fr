---
title: À l’aide de la règle définit pour spécifier les règles C++ à exécuter | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac3877e6-5349-4c03-9541-3d5be259f1e8
caps.latest.revision: 7
author: corob-msft
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d2b3aed9e2504011a61fe13acdf4a836cb41f8df
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49859666"
---
# <a name="using-rule-sets-to-specify-the-c-rules-to-run"></a>Utilisation des ensembles de règles pour spécifier les règles C++ à exécuter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] et [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)], vous pouvez créer et modifier un personnalisé *ensemble de règles* pour répondre aux besoins spécifiques de projet associés à l’analyse du code. Pour créer une règle de C++ personnalisée défini, un projet C/C++ doit être ouvert dans l’IDE Visual Studio. Vous puis ouvrez un ensemble de règles standard dans l’éditeur d’ensemble de règles et puis ajoutez ou supprimez des règles spécifiques et éventuellement modifiez l’action qui se produit lorsque l’analyse du code détermine qu’une règle a été violée.  
  
 Pour créer une nouvelle règle personnalisée définie, vous l’enregistrez à l’aide d’un nouveau nom de fichier. L’ensemble de règles personnalisé est automatiquement affecté au projet.  
  
## <a name="opening-the-rule-set-editor"></a>Ouverture de la règle d’éditeur d’ensembles  
  
#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Pour créer une règle personnalisée à partir d’un seul ensemble de règles existant  
  
1. Dans l’Explorateur de solutions, ouvrez le menu contextuel du projet, puis choisissez **propriétés**.  
  
2. Sur le **propriétés** , choisir **analyse du Code**.  
  
3. Dans le **l’ensemble de règles** liste déroulante, effectuez l’une des opérations suivantes :  
  
   - Choisissez l’ensemble de règles que vous souhaitez personnaliser.  
  
     \- ou -  
  
   - Choisissez  **\<Parcourir... >** pour spécifier une règle existante définie qui n’est pas dans la liste.  
  
4. Choisissez **Open** pour afficher les règles dans l’éditeur d’ensemble de règles.  
  
#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Pour modifier une règle définie dans l’éditeur d’ensemble de règles  
  
-   Pour modifier le nom complet de l’ensemble de règles, dans le **vue** menu, choisissez **fenêtre Propriétés**. Entrez le nom d’affichage dans le **nom** boîte. Notez que le nom de l’affichage peut différer du nom du fichier.  
  
-   Pour ajouter toutes les règles du groupe à un ensemble de règles personnalisé, sélectionnez la case à cocher du groupe. Pour supprimer toutes les règles du groupe, désactivez la case à cocher.  
  
-   Pour ajouter une règle spécifique à l’ensemble de règles personnalisé, sélectionnez la case à cocher de la règle. Pour supprimer la règle à partir de l’ensemble de règles, désactivez la case à cocher.  
  
-   Pour modifier l’action effectuée lorsqu’une règle est violée dans une analyse du code, choisissez la **Action** champ pour la règle et choisissez l’une des valeurs suivantes :  
  
     **Avertir** -génère un avertissement.  
  
     **Erreur** -génère une erreur.  
  
     **Aucun** -désactive la règle. Cette action est le même que la suppression de la règle de l’ensemble de règles.  
  
#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Pour regrouper, filtrer ou modifier les champs dans l’éditeur d’ensemble de règles à l’aide de la barre d’outils Éditeur de règle ensemble  
  
-   Pour développer les règles dans tous les groupes, choisissez **développer tout**.  
  
-   Pour réduire les règles dans tous les groupes, choisissez **réduire tout**.  
  
-   Pour modifier le champ dont les règles sont regroupés, choisissez le champ à partir de la **Group By** liste. Pour afficher les règles non groupées, choisissez  **\<None >**.  
  
-   Pour ajouter ou supprimer des champs dans les colonnes de la règle, choisissez **Options de colonne**.  
  
-   Pour masquer les règles qui ne s’appliquent pas à la solution actuelle, choisissez **masquer des règles qui ne s’appliquent pas à la solution actuelle**.  
  
-   Pour basculer entre l’affichage et masquage des règles qui sont affectés à l’action d’erreur, choisissez **afficher les règles qui peuvent générer des erreurs d’analyse du Code**.  
  
-   Pour basculer entre l’affichage et masquage des règles qui sont affectés à l’action de l’avertissement, choisissez **afficher les règles qui peuvent générer des avertissements d’analyse du Code**.  
  
-   Pour basculer entre l’affichage et masquage des règles qui sont affectées la **aucun** action, choisissez **afficher les règles qui ne sont pas activés**.  
  
-   Pour ajouter ou supprimer des ensembles de règles de valeur par défaut à l’ensemble de règles actuel de Microsoft, choisissez **ajouter ou supprimer des ensembles de règles enfants**.



