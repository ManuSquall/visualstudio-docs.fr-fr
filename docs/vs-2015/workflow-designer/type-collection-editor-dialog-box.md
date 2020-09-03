---
title: Éditeur de collections de types, boîte de dialogue | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: dae99166b8b811df75f2e2777d176e6778b60c7d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670146"
---
# <a name="type-collection-editor-dialog-box"></a>Boîte de dialogue Éditeur de collections de types
La boîte de dialogue **éditeur de collections de types** permet d’ajouter des types connus aux activités d' **envoi** et de **réception** . Cette boîte de dialogue est également utilisée pour ajouter des arguments de type générique à l’activité **InvokeMethod** . Lorsqu’il est utilisé pour les activités d' **envoi** et de **réception** pour ajouter des types connus, la boîte de dialogue **éditeur de collections de types** requiert que les ajouts de types soient uniques. Si un type en double est ajouté et que la modification est validée en cliquant sur **OK**, un message d’erreur est retourné. Lorsqu’il est utilisé pour que l’activité **InvokeMethod** ajoute des arguments de type générique, la boîte de dialogue **éditeur de collections de types** permet l’ajout de types en double.

> [!NOTE]
> [!INCLUDE[crabout](../includes/crabout-md.md)] les types connus, consultez [Data Contract Known Types](https://msdn.microsoft.com/library/1a0baea1-27b7-470d-9136-5bbad86c4337).

 Le tableau suivant décrit les éléments d’interface utilisateur de la boîte de dialogue **type de collection** .

|Élément de l’interface utilisateur|Description|
|----------------|-----------------|
|**Type List**|Liste des types qui ont été ajoutés ou supprimés.|

## <a name="to-bring-up-the-type-collection-editor"></a>Pour afficher l’Éditeur de collections de types

#### <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>Pour afficher l'Éditeur de collections de types pour les activités Send et Receive

1. Sélectionnez l’activité **Envoyer** ou **recevoir** en mode conception.

2. Appuyez sur **F4** pour afficher la fenêtre **Propriétés** .

3. Dans la fenêtre **Propriétés** , cliquez sur le bouton de sélection en regard de la propriété **KnownTypes** .

#### <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>Pour afficher l'Éditeur de collections de types pour l'activité InvokeMethod

1. Sélectionnez l’activité **InvokeMethod** en mode Design.

2. Appuyez sur **F4** pour afficher la fenêtre **Propriétés** .

3. Dans la fenêtre **Propriétés** , cliquez sur le bouton de sélection en regard de la propriété **genericTypeArguments** .