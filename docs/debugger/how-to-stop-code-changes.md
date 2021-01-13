---
title: Arrêter les modifications du code | Microsoft Docs
description: Découvrez comment arrêter l’application des modifications du code tout en utilisant la fonctionnalité Modifier & continuer pendant une session de débogage Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Stop Applying Code Changes command
- code changes, stopping application of
- Edit and Continue, stopping code changes
ms.assetid: 9e72a50c-bb0a-4eaa-9ac1-d00930b68d38
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a63a15340c597a7b62735dfb3f6f14d3707262ac
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150702"
---
# <a name="how-to-stop-code-changes"></a>Comment : arrêter des modifications de code
Pendant que Modifier & Continuer est en train d'appliquer les modifications du code, vous pouvez arrêter l'opération.

> [!CAUTION]
> L'arrêt des modifications du code dans du code managé peut produire des résultats inattendus. L'application de modifications à du code managé est normalement un processus rapide ; il est donc rare de devoir arrêter ce type de modifications.

### <a name="to-stop-applying-code-changes"></a>Pour arrêter d'appliquer les modifications du code

- Dans le menu **Déboguer**, cliquez sur **Cesser d’appliquer les modifications du code**.

  Cet élément de menu est visible uniquement lorsque les modifications du code sont appliquées.

  Si vous choisissez cette option, aucune modification du code n'est validée.

## <a name="see-also"></a>Voir aussi
- [Modifier &amp; Continuer](../debugger/edit-and-continue.md)
- [Modifier & Continuer, Débogage, Boîte de dialogue Options](./edit-and-continue.md)