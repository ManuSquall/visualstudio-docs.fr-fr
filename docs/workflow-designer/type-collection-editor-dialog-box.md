---
title: Boîte de dialogue de l’éditeur de collections type | Documents Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 77de1cdcffc1303a439afe743cdfd52b121779d7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="type-collection-editor-dialog-box"></a>Boîte de dialogue Éditeur de collections de types

Le **éditeur de collections Type** boîte de dialogue permet d’ajouter des types connus pour le **envoyer** et **réception** activités. Cette boîte de dialogue est également utilisé pour ajouter des arguments de type générique pour le **InvokeMethod** activité. Lorsqu’il est utilisé pour le **envoyer** et **réception** activités à ajouter des types connus, le **éditeur de collections Type** boîte de dialogue requiert les ajouts de types soient uniques. Si un type en double est ajouté et que la modification est validée en cliquant sur **OK**, un message d’erreur est retourné. Lorsqu’il est utilisé pour le **InvokeMethod** activité pour ajouter des arguments de type générique, la **éditeur de collections Type** boîte de dialogue autorise l’ajout de types en double.

Pour plus d’informations, consultez [types connus de contrat de données](/dotnet/framework/wcf/feature-details/data-contract-known-types).

Le tableau suivant décrit les éléments d’interface utilisateur utilisateur de la **Type de Collection** boîte de dialogue.

|Élément d'interface utilisateur|Description|
|----------------|-----------------|
|**Liste de types**|Liste des types qui ont été ajoutés ou supprimés.|

## <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>Pour afficher l’Éditeur de collections de types pour les activités Send et Receive

1.  Sélectionnez le **envoyer** ou **réception** activité en mode design.

2.  Appuyez sur **F4** pour afficher les **propriétés** fenêtre.

3.  Dans le **propriétés** fenêtre, cliquez sur le bouton de sélection en regard du **KnownTypes** propriété.

## <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>Pour afficher l’Éditeur de collections de types pour l’activité InvokeMethod

1.  Sélectionnez le **InvokeMethod** activité en mode design.

2.  Appuyez sur **F4** pour afficher les **propriétés** fenêtre.

3.  Dans le **propriétés** fenêtre, cliquez sur le bouton de sélection en regard du **GenericTypeArguments** propriété.