---
title: Déploiement du shell VS
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 61cf6e716f082abf28043d56d1a8803853d894aa
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39566671"
---
# <a name="vs-shell-deployment"></a>Déploiement du shell VS

Un interpréteur de commandes isolé vous permet de déterminer où Visual Studio des fonctionnalités que vous avez besoin interagir avec votre langage spécifique à un domaine et la manière dont cette solution doit apparaître. Pour plus d’informations sur le shell isolé Visual Studio, consultez [personnalisation du Shell isolé](../extensibility/customizing-the-isolated-shell.md).

## <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Pour définir un Shell Visual Studio comme cible de déploiement

1.  Dans le **DslPackage** projet, ouvrez **source.extension.tt**.

2.  Sous `<SupportedProducts>` insérer :

    ```xml
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
    ```

     Remplacez *MyIsolatedShell* avec le nom de votre package de shell isolé.