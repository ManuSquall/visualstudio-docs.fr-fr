---
title: Déploiement de VS Shell | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 4964ce162efac640ea7581b4d3f26f3d50087319
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
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