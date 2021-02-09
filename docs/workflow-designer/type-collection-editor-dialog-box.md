---
title: Éditeur de collections de type Concepteur de flux de travail (boîte de dialogue)
description: Découvrez comment vous pouvez utiliser la boîte de dialogue Éditeur de collections de types pour ajouter des types connus aux activités d’envoi et de réception.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b8f194ee792f2a60df71a78af6f41e45aaac91da
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875261"
---
# <a name="type-collection-editor-dialog-box"></a>Boîte de dialogue Éditeur de collections de types

La boîte de dialogue **éditeur de collections de types** permet d’ajouter des types connus aux activités d' **envoi** et de **réception** . Cette boîte de dialogue est également utilisée pour ajouter des arguments de type générique à l’activité **InvokeMethod** . Lorsqu’il est utilisé pour les activités d' **envoi** et de **réception** pour ajouter des types connus, la boîte de dialogue **éditeur de collections de types** requiert que les ajouts de types soient uniques. Si un type en double est ajouté et que la modification est validée en cliquant sur **OK**, un message d’erreur est retourné. Lorsqu’il est utilisé pour que l’activité **InvokeMethod** ajoute des arguments de type générique, la boîte de dialogue **éditeur de collections de types** permet l’ajout de types en double.

Pour plus d’informations, consultez [types connus de contrat de données](/dotnet/framework/wcf/feature-details/data-contract-known-types).

Le tableau suivant décrit les éléments d’interface utilisateur de la boîte de dialogue **type de collection** .

|Élément de l’interface utilisateur|Description|
|-|-----------------|
|**Type List**|Liste des types qui ont été ajoutés ou supprimés.|

## <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>Pour afficher l'Éditeur de collections de types pour les activités Send et Receive

1. Sélectionnez l’activité **Envoyer** ou **recevoir** en mode conception.

2. Appuyez sur **F4** pour afficher la fenêtre **Propriétés** .

3. Dans la fenêtre **Propriétés** , cliquez sur le bouton de sélection en regard de la propriété **KnownTypes** .

## <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>Pour afficher l'Éditeur de collections de types pour l'activité InvokeMethod

1. Sélectionnez l’activité **InvokeMethod** en mode Design.

2. Appuyez sur **F4** pour afficher la fenêtre **Propriétés** .

3. Dans la fenêtre **Propriétés** , cliquez sur le bouton de sélection en regard de la propriété **genericTypeArguments** .
