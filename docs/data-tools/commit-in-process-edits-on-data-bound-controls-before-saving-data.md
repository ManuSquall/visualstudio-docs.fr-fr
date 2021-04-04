---
title: Modifications non validées
description: Valider des modifications in-process sur des contrôles de Windows Forms liés aux données avant d’enregistrer des données. Appelez la fonction EndEdit pour tous les composants BindingSource sur un formulaire.
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
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 53101505230a51f109ace904c2f8322659733b4b
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216317"
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

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb" id="Snippet1":::

2. Ajoutez la ligne de code suivante immédiatement avant les appels pour enregistrer les données du formulaire ( `TableAdapterManager.UpdateAll()` méthode) :

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb" id="Snippet2":::

## <a name="see-also"></a>Voir aussi

- [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Mise à jour hiérarchique](../data-tools/hierarchical-update.md)
