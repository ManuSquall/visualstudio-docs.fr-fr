---
title: Modifications non validées
description: Valider les modifications in-process sur les contrôles liés aux données avant d’enregistrer
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- committing edited records
- data-bound controls, in-process edits
- DataBinding class, committing edited records
- hierarchical update, committing edited records
- BindingSource class, committing edited records
- EndEdit method
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4e2188e20b2ba36a6ef3805faab9f80c4379f1f7
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90038372"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Valider des modifications in-process sur des contrôles liés aux données avant d’enregistrer des données

Lors de la modification des valeurs dans les contrôles liés aux données, les utilisateurs doivent naviguer dans l’enregistrement actuel pour valider la valeur mise à jour dans la source de données sous-jacente à laquelle le contrôle est lié. Lorsque vous faites glisser des éléments depuis la [fenêtre sources de données](add-new-data-sources.md) vers un formulaire, le premier élément que vous supprimez génère du code dans l’événement de clic du bouton **Enregistrer** du <xref:System.Windows.Forms.BindingNavigator> . Ce code appelle la <xref:System.Windows.Forms.BindingSource.EndEdit%2A> méthode de <xref:System.Windows.Forms.BindingSource> . Par conséquent, l’appel à la <xref:System.Windows.Forms.BindingSource.EndEdit%2A> méthode est généré uniquement pour le premier <xref:System.Windows.Forms.BindingSource> ajouté au formulaire.

L’appel de <xref:System.Windows.Forms.BindingSource.EndEdit%2A> valide toutes les modifications en cours de tous les contrôles liés aux données modifiés. Par conséquent, si un contrôle lié aux données a encore le focus et que vous cliquez sur le bouton **Enregistrer**, toutes les modifications en attente dans ce contrôle sont validées avant l’enregistrement réel (la méthode `TableAdapterManager.UpdateAll`).

Vous pouvez configurer votre application pour qu’elle valide automatiquement les modifications, même si un utilisateur tente d’enregistrer des données sans valider les modifications, dans le cadre du processus d’enregistrement.

> [!NOTE]
> Le concepteur ajoute le `BindingSource.EndEdit` code uniquement pour le premier élément déposé dans un formulaire. Par conséquent, vous devez ajouter une ligne de code pour appeler la <xref:System.Windows.Forms.BindingSource.EndEdit%2A> méthode pour chaque <xref:System.Windows.Forms.BindingSource> sur le formulaire. Vous pouvez ajouter manuellement une ligne de code pour appeler la <xref:System.Windows.Forms.BindingSource.EndEdit%2A> méthode pour chaque <xref:System.Windows.Forms.BindingSource> . Vous pouvez également ajouter la `EndEditOnAllBindingSources` méthode au formulaire et l’appeler avant d’effectuer un enregistrement.

Le code suivant utilise une requête [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/) pour itérer tous les <xref:System.Windows.Forms.BindingSource> composants et appeler la <xref:System.Windows.Forms.BindingSource.EndEdit%2A> méthode pour chaque <xref:System.Windows.Forms.BindingSource> sur un formulaire.

## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Pour appeler EndEdit pour tous les composants BindingSource sur un formulaire

1. Ajoutez le code suivant au formulaire qui contient les <xref:System.Windows.Forms.BindingSource> composants.

     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.vb)]

2. Ajoutez la ligne de code suivante immédiatement avant les appels pour enregistrer les données du formulaire ( `TableAdapterManager.UpdateAll()` méthode) :

     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.vb)]

## <a name="see-also"></a>Voir aussi

- [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Mise à jour hiérarchique](../data-tools/hierarchical-update.md)
