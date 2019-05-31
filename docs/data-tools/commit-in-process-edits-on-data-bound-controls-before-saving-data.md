---
title: Valider des modifications in-process sur des contrôles liés aux données avant l’enregistrement
ms.date: 11/04/2016
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 129ab5be6264f566de284b2736664c8c0d8c07d7
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66261837"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Valider des modifications in-process sur des contrôles liés aux données avant d’enregistrer des données

Lorsque vous modifiez les valeurs dans des contrôles liés aux données, les utilisateurs doivent sortir pour valider la valeur mise à jour dans la source de données sous-jacente, le contrôle est lié à l’enregistrement en cours. Lorsque vous faites glisser des éléments à partir de la [fenêtre Sources de données](add-new-data-sources.md) sur un formulaire, le premier élément que vous déposez génère du code dans le **enregistrer** événement de clic du bouton du <xref:System.Windows.Forms.BindingNavigator>. Ce code appelle la <xref:System.Windows.Forms.BindingSource.EndEdit%2A> méthode de la <xref:System.Windows.Forms.BindingSource>. Par conséquent, l’appel à la <xref:System.Windows.Forms.BindingSource.EndEdit%2A> méthode est générée uniquement pour la première <xref:System.Windows.Forms.BindingSource> qui est ajouté au formulaire.

L’appel de <xref:System.Windows.Forms.BindingSource.EndEdit%2A> valide toutes les modifications en cours de tous les contrôles liés aux données modifiés. Par conséquent, si un contrôle lié aux données a encore le focus et que vous cliquez sur le bouton **Enregistrer**, toutes les modifications en attente dans ce contrôle sont validées avant l’enregistrement réel (la méthode `TableAdapterManager.UpdateAll`).

Vous pouvez configurer votre application pour valider automatiquement les modifications, même si un utilisateur tente d’enregistrer des données sans valider les modifications, dans le cadre de l’enregistrement processus.

> [!NOTE]
> Le concepteur ajoute le `BindingSource.EndEdit` code uniquement pour le premier élément déposé sur un formulaire. Par conséquent, vous devez ajouter une ligne de code pour appeler le <xref:System.Windows.Forms.BindingSource.EndEdit%2A> méthode pour chaque <xref:System.Windows.Forms.BindingSource> sur le formulaire. Vous pouvez ajouter manuellement une ligne de code pour appeler le <xref:System.Windows.Forms.BindingSource.EndEdit%2A> méthode pour chaque <xref:System.Windows.Forms.BindingSource>. Vous pouvez également ajouter le `EndEditOnAllBindingSources` méthode au formulaire et appelez-le avant d’effectuer une sauvegarde.

Le code suivant utilise un [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/) requête pour effectuer une itération de tous les <xref:System.Windows.Forms.BindingSource> composants et appelez le <xref:System.Windows.Forms.BindingSource.EndEdit%2A> méthode pour chaque <xref:System.Windows.Forms.BindingSource> sur un formulaire.

## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Pour appeler EndEdit pour tous les composants BindingSource sur un formulaire

1. Ajoutez le code suivant au formulaire qui contienne le <xref:System.Windows.Forms.BindingSource> composants.

     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.vb)]

2. Ajoutez la ligne suivante de code immédiatement avant tous les appels pour enregistrer les données du formulaire (le `TableAdapterManager.UpdateAll()` (méthode)) :

     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.vb)]

## <a name="see-also"></a>Voir aussi

- [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Mise à jour hiérarchique](../data-tools/hierarchical-update.md)