---
title: Boîte de dialogue Éditeur de Collection de type | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 34b8129b5a0b1fe27a7e4e6c178ddace638e5ffc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47495904"
---
# <a name="type-collection-editor-dialog-box"></a>Boîte de dialogue Éditeur de collections de types
Le **éditeur de collections de Type** boîte de dialogue est utilisée pour ajouter des types connus le **envoyer** et **réception** activités. Cette boîte de dialogue est également utilisé pour ajouter des arguments de type générique pour le **InvokeMethod** activité. Lorsqu’il est utilisé pour le **envoyer** et **réception** activités à ajouter des types connus, le **éditeur de collections de Type** boîte de dialogue nécessite les ajouts de type unique. Si un type en double est ajouté et la modification est validée en cliquant sur **OK**, un message d’erreur est retourné. Lorsqu’il est utilisé pour le **InvokeMethod** activité pour ajouter des arguments de type générique, le **éditeur de collections de Type** boîte de dialogue permet l’ajout de types en double.  
  
> [!NOTE]
>  [!INCLUDE[crabout](../includes/crabout-md.md)] types connus, consultez [Data Contract Known Types](http://msdn.microsoft.com/library/1a0baea1-27b7-470d-9136-5bbad86c4337).  
  
 Le tableau suivant décrit les éléments d’interface utilisateur utilisateur de la **Type Collection** boîte de dialogue.  
  
|Élément d'interface utilisateur|Description|  
|----------------|-----------------|  
|**Liste de types**|Liste des types qui ont été ajoutés ou supprimés.|  
  
## <a name="to-bring-up-the-type-collection-editor"></a>Pour afficher l'Éditeur de collections de types  
  
#### <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>Pour afficher l’Éditeur de collections de types pour les activités Send et Receive  
  
1.  Sélectionnez le **envoyer** ou **réception** activité en mode design.  
  
2.  Appuyez sur **F4** pour faire apparaître le **propriétés** fenêtre.  
  
3.  Dans le **propriétés** , cliquez sur le bouton de sélection en regard du **KnownTypes** propriété.  
  
#### <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>Pour afficher l’Éditeur de collections de types pour l’activité InvokeMethod  
  
1.  Sélectionnez le **InvokeMethod** activité en mode design.  
  
2.  Appuyez sur **F4** pour faire apparaître le **propriétés** fenêtre.  
  
3.  Dans le **propriétés** , cliquez sur le bouton de sélection en regard du **GenericTypeArguments** propriété.