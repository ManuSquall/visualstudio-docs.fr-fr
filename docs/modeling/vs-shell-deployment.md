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
ms.openlocfilehash: e7df1991832e954def71a6cee5bd5516dfd4e961
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="vs-shell-deployment"></a>Déploiement du shell VS

Un shell isolé vous permet de déterminer où Visual Studio fonctionnalités que vous devez interagir avec votre langage spécifique à un domaine et comment cette solution doit s’afficher. Pour plus d’informations sur le shell isolé Visual Studio, consultez [personnalisation le Shell isolé](../extensibility/customizing-the-isolated-shell.md).

## <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Pour définir un interpréteur de commandes Visual Studio en tant que la cible de déploiement

1.  Dans le **DslPackage** projet, ouvrez **source.extension.tt**.

2.  Sous `<SupportedProducts>` insérer :

    ```
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
    ```

     Remplacez *MyIsolatedShell* avec le nom de votre package de shell isolé.