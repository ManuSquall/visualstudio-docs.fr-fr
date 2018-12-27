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
ms.openlocfilehash: 663e706dba9ec7b6479e3e9360ef8aa2d12b1400
ms.sourcegitcommit: 159ed9d4f56cdc1dff2fd19d9dffafe77e46cd4e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2018
ms.locfileid: "53739495"
---
# <a name="vs-shell-deployment"></a>Déploiement du shell VS

Un interpréteur de commandes isolé vous permet de déterminer où Visual Studio des fonctionnalités que vous avez besoin interagir avec votre langage spécifique à un domaine et la manière dont cette solution doit apparaître. Pour plus d’informations sur le shell isolé Visual Studio, consultez [personnalisation du Shell isolé](https://vspartner.com/pages/vsshells).

Pour définir un Shell Visual Studio comme cible de déploiement :

1. Dans le **DslPackage** projet, ouvrez **source.extension.tt**.

2. Sous `<SupportedProducts>` insérer :

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Remplacez *MyIsolatedShell* avec le nom de votre package de shell isolé.