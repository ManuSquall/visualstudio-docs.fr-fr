---
title: Valider des modifications in-process sur des contrôles liés aux données avant d’enregistrer des données | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- committing edited records
- data-bound controls, in-process edits
- DataBinding class, committing edited records
- hierarchical update, committing edited records
- BindingSource class, committing edited records
- EndEdit method
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3867b91a8b417b5670514b66aaf93fdab4e9618c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662447"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Valider des modifications in-process sur des contrôles liés aux données avant d’enregistrer des données
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lors de la modification des valeurs dans les contrôles liés aux données, les utilisateurs doivent naviguer dans l’enregistrement actuel pour valider la valeur mise à jour dans la source de données sous-jacente à laquelle le contrôle est lié. Lorsque vous faites glisser des éléments depuis la [fenêtre sources de données](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) vers un formulaire, le premier élément que vous supprimez génère du code dans l’événement de clic du bouton **Enregistrer** du <xref:System.Windows.Forms.BindingNavigator> . Ce code appelle la <xref:System.Windows.Forms.BindingSource.EndEdit%2A> méthode de <xref:System.Windows.Forms.BindingSource> . Par conséquent, l’appel à la <xref:System.Windows.Forms.BindingSource.EndEdit%2A> méthode est généré uniquement pour le premier <xref:System.Windows.Forms.BindingSource> ajouté au formulaire.

 L’appel de <xref:System.Windows.Forms.BindingSource.EndEdit%2A> valide toutes les modifications en cours de tous les contrôles liés aux données modifiés. Par conséquent, si un contrôle lié aux données a encore le focus et que vous cliquez sur le bouton **Enregistrer**, toutes les modifications en attente dans ce contrôle sont validées avant l’enregistrement réel (la méthode `TableAdapterManager.UpdateAll`).

 Vous pouvez configurer votre application pour qu’elle valide automatiquement les modifications, même si un utilisateur tente d’enregistrer des données sans valider les modifications, dans le cadre du processus d’enregistrement.

> [!NOTE]
> Le concepteur ajoute le `BindingSource.EndEdit` code uniquement pour le premier élément déposé dans un formulaire. Par conséquent, vous devez ajouter une ligne de code pour appeler la <xref:System.Windows.Forms.BindingSource.EndEdit%2A> méthode pour chaque <xref:System.Windows.Forms.BindingSource> sur le formulaire. Vous pouvez ajouter manuellement une ligne de code pour appeler la <xref:System.Windows.Forms.BindingSource.EndEdit%2A> méthode pour chaque <xref:System.Windows.Forms.BindingSource> . Vous pouvez également ajouter la `EndEditOnAllBindingSources` méthode au formulaire et l’appeler avant d’effectuer un enregistrement.

 Le code suivant utilise une requête [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) pour itérer tous les <xref:System.Windows.Forms.BindingSource> composants et appeler la <xref:System.Windows.Forms.BindingSource.EndEdit%2A> méthode pour chaque <xref:System.Windows.Forms.BindingSource> sur un formulaire.

## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Pour appeler EndEdit pour tous les composants BindingSource sur un formulaire

1. Ajoutez le code suivant au formulaire qui contient les <xref:System.Windows.Forms.BindingSource> composants.

     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs#1)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb#1)]

2. Ajoutez la ligne de code suivante immédiatement avant les appels pour enregistrer les données du formulaire ( `TableAdapterManager.UpdateAll()` méthode) :

     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs#2)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb#2)]

## <a name="see-also"></a>Voir aussi
 [Lier des contrôles de Windows Forms à des données dans](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) la [mise à jour hiérarchique](../data-tools/hierarchical-update.md) de Visual Studio
