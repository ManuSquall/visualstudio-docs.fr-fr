---
title: Concepteur de flux de travail - boîte de dialogue Éditeur de Collection de Type
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 09bb5c7789be78a39a8d33a556ce66385db4a1d8
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31973012"
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