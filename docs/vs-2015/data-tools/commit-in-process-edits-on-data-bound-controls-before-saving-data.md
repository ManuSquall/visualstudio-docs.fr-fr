---
title: Valider des modifications in-process sur des contrôles liés aux données avant d’enregistrer des données | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- commiting edited records
- data-bound controls, in-process edits
- DataBinding class, commiting edited records
- hierarchical update, commiting edited records
- BindingSource class, commiting edited records
- EndEdit method
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3af1534e6436eec2eac1f294be8c2428c949ce9d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49296027"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Valider des modifications in-process sur des contrôles liés aux données avant d’enregistrer des données
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Lorsque vous modifiez les valeurs dans des contrôles liés aux données, les utilisateurs doivent sortir pour valider la valeur mise à jour dans la source de données sous-jacente, le contrôle est lié à l’enregistrement en cours. Lorsque vous faites glisser des éléments à partir de la [fenêtre Sources de données](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) sur un formulaire, le premier élément que vous déposez génère du code dans le **enregistrer** événement de clic du bouton du <xref:System.Windows.Forms.BindingNavigator>. Ce code appelle la <xref:System.Windows.Forms.BindingSource.EndEdit%2A> méthode de la <xref:System.Windows.Forms.BindingSource>. Par conséquent, l’appel à la <xref:System.Windows.Forms.BindingSource.EndEdit%2A> méthode est générée uniquement pour la première <xref:System.Windows.Forms.BindingSource> qui est ajouté au formulaire.  
  
 Le <xref:System.Windows.Forms.BindingSource.EndEdit%2A> appel valide toutes les modifications qui se trouvent dans le processus, dans tous les contrôles liés aux données qui sont actuellement en cours de modification. Par conséquent, si un contrôle lié aux données a encore le focus et que vous cliquez sur le **enregistrer** bouton, toutes les modifications en attente dans ce contrôle sont validées avant l’enregistrement réel (le `TableAdapterManager.UpdateAll` méthode).  
  
 Vous pouvez configurer votre application pour valider automatiquement les modifications, même si un utilisateur tente d’enregistrer des données sans valider les modifications, dans le cadre de l’enregistrement processus.  
  
> [!NOTE]
>  Le concepteur ajoute le `BindingSource.EndEdit` code uniquement pour le premier élément déposé sur un formulaire. Par conséquent, vous devez ajouter une ligne de code pour appeler le <xref:System.Windows.Forms.BindingSource.EndEdit%2A> méthode pour chaque <xref:System.Windows.Forms.BindingSource> sur le formulaire. Vous pouvez ajouter manuellement une ligne de code pour appeler le <xref:System.Windows.Forms.BindingSource.EndEdit%2A> méthode pour chaque <xref:System.Windows.Forms.BindingSource>. Vous pouvez également ajouter le `EndEditOnAllBindingSources` méthode au formulaire et appelez-le avant d’effectuer une sauvegarde.  
  
 Le code suivant utilise un [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) requête pour effectuer une itération de tous les <xref:System.Windows.Forms.BindingSource> composants et appelez le <xref:System.Windows.Forms.BindingSource.EndEdit%2A> méthode pour chaque <xref:System.Windows.Forms.BindingSource> sur un formulaire.  
  
## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Pour appeler EndEdit pour tous les composants BindingSource sur un formulaire  
  
1.  Ajoutez le code suivant au formulaire qui contienne le <xref:System.Windows.Forms.BindingSource> composants.  
  
     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs#1)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb#1)]  
  
2.  Ajoutez la ligne suivante de code immédiatement avant tous les appels pour enregistrer les données du formulaire (le `TableAdapterManager.UpdateAll()` (méthode)) :  
  
     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs#2)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb#2)]  
  
## <a name="see-also"></a>Voir aussi  
 [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Mise à jour hiérarchique](../data-tools/hierarchical-update.md)

