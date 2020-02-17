---
title: Utilisation d’ensembles de règles pour C++ spécifier les règles à exécuter | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: ac3877e6-5349-4c03-9541-3d5be259f1e8
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: ff105af1d817613b324e1158130457eb906c753f
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77277853"
---
# <a name="using-rule-sets-to-specify-the-c-rules-to-run"></a>Utilisation des ensembles de règles pour spécifier les règles C++ à exécuter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] et [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)], vous pouvez créer et modifier un *ensemble de règles* personnalisé pour répondre à des besoins de projet spécifiques associés à l’analyse du code. Pour créer un ensemble C++ de règles personnalisé, un projetC++ C/doit être ouvert dans l’IDE de Visual Studio. Vous ouvrez ensuite un ensemble de règles standard dans l’éditeur d’ensembles de règles, puis vous ajoutez ou supprimez des règles spécifiques et modifiez éventuellement l’action qui se produit lorsque l’analyse du code détermine qu’une règle a été violée.  
  
 Pour créer un ensemble de règles personnalisé, enregistrez-le à l’aide d’un nouveau nom de fichier. L’ensemble de règles personnalisé est automatiquement affecté au projet.  
  
## <a name="opening-the-rule-set-editor"></a>Ouverture de l’éditeur d’ensembles de règles  
  
#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Pour créer une règle personnalisée à partir d’un seul ensemble de règles existant  
  
1. Dans Explorateur de solutions, ouvrez le menu contextuel du projet, puis choisissez **Propriétés**.  
  
2. Sous l’onglet **Propriétés** , choisissez **analyse du code**.  
  
3. Dans la liste déroulante **ensemble de règles** , effectuez l’une des opérations suivantes :  
  
   - Choisissez l’ensemble de règles que vous souhaitez personnaliser.  
  
     \- ou -  
  
   - Choisir **\<parcourir... >** pour spécifier un ensemble de règles existant qui ne figure pas dans la liste.  
  
4. Choisissez **ouvrir** pour afficher les règles dans l’éditeur d’ensembles de règles.  
  
#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Pour modifier un ensemble de règles dans l’éditeur d’ensembles de règles  
  
- Pour modifier le nom complet de l’ensemble de règles, dans le menu **affichage** , choisissez **fenêtre Propriétés**. Entrez le nom d’affichage dans la zone **nom** . Notez que le nom d’affichage peut être différent du nom de fichier.  
  
- Pour ajouter toutes les règles du groupe à un ensemble de règles personnalisé, activez la case à cocher du groupe. Pour supprimer toutes les règles du groupe, désactivez la case à cocher.  
  
- Pour ajouter une règle spécifique à l’ensemble de règles personnalisé, activez la case à cocher de la règle. Pour supprimer la règle de l’ensemble de règles, désactivez la case à cocher.  
  
- Pour modifier l’action entreprise lorsqu’une règle est violée dans une analyse du code, choisissez le champ **action** pour la règle, puis choisissez l’une des valeurs suivantes :  
  
     **WARN** -génère un avertissement.  
  
     **Erreur** : génère une erreur.  
  
     **None** : désactive la règle. Cette action revient à supprimer la règle de l’ensemble de règles.  
  
#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Pour regrouper, filtrer ou modifier les champs de l’éditeur d’ensembles de règles à l’aide de la barre d’outils Éditeur d’ensemble de règles  
  
- Pour développer les règles de tous les groupes, choisissez **développer tout**.  
  
- Pour réduire les règles de tous les groupes, choisissez **réduire tout**.  
  
- Pour modifier le champ par lequel les règles sont regroupées, choisissez le champ dans la liste **regrouper par** . Pour afficher les règles non groupées, choisissez **\<aucun >** .  
  
- Pour ajouter ou supprimer des champs dans les colonnes de règles, choisissez **options de colonne**.  
  
- Pour masquer les règles qui ne s’appliquent pas à la solution actuelle, choisissez **Masquer les règles qui ne s’appliquent pas à la solution actuelle**.  
  
- Pour basculer entre l’affichage et le masquage des règles affectées par l’action d’erreur, choisissez **afficher les règles qui peuvent générer des erreurs d’analyse du code**.  
  
- Pour basculer entre l’affichage et le masquage des règles affectées par l’action d’avertissement, choisissez **afficher les règles qui peuvent générer des avertissements d’analyse du code**.  
  
- Pour basculer entre l’affichage et le masquage des règles affectées par l’action **aucun** , choisissez **afficher les règles qui ne sont pas activées**.  
  
- Pour ajouter ou supprimer des ensembles de règles par défaut Microsoft pour l’ensemble de règles actuel, choisissez **Ajouter ou supprimer des ensembles de règles enfants**.
