---
title: Concepteur de flux de travail - boîte de dialogue Éditeur de Collection de Type
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 191635364c445bc3959ee2f5f63c7c72c71f171d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60093122"
---
# <a name="type-collection-editor-dialog-box"></a>Boîte de dialogue Éditeur de collections de types

Le **éditeur de collections de Type** boîte de dialogue est utilisée pour ajouter des types connus le **envoyer** et **réception** activités. Cette boîte de dialogue est également utilisé pour ajouter des arguments de type générique pour le **InvokeMethod** activité. Lorsqu’il est utilisé pour le **envoyer** et **réception** activités à ajouter des types connus, le **éditeur de collections de Type** boîte de dialogue nécessite les ajouts de type unique. Si un type en double est ajouté et la modification est validée en cliquant sur **OK**, un message d’erreur est retourné. Lorsqu’il est utilisé pour le **InvokeMethod** activité pour ajouter des arguments de type générique, le **éditeur de collections de Type** boîte de dialogue permet l’ajout de types en double.

Pour plus d’informations, consultez [types connus de contrats de données](/dotnet/framework/wcf/feature-details/data-contract-known-types).

Le tableau suivant décrit les éléments d’interface utilisateur utilisateur de la **Type Collection** boîte de dialogue.

|Élément d'interface utilisateur|Description|
|-|-----------------|
|**Liste de types**|Liste des types qui ont été ajoutés ou supprimés.|

## <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>Pour afficher l'Éditeur de collections de types pour les activités Send et Receive

1. Sélectionnez le **envoyer** ou **réception** activité en mode design.

2. Appuyez sur **F4** pour faire apparaître le **propriétés** fenêtre.

3. Dans le **propriétés** , cliquez sur le bouton de sélection en regard du **KnownTypes** propriété.

## <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>Pour afficher l'Éditeur de collections de types pour l'activité InvokeMethod

1. Sélectionnez le **InvokeMethod** activité en mode design.

2. Appuyez sur **F4** pour faire apparaître le **propriétés** fenêtre.

3. Dans le **propriétés** , cliquez sur le bouton de sélection en regard du **GenericTypeArguments** propriété.