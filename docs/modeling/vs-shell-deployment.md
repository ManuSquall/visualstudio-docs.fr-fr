---
title: Déploiement du shell VS
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d8793312e0ed022fc7210508efdf20a81b293f0f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535848"
---
# <a name="vs-shell-deployment"></a>Déploiement du shell VS

Un interpréteur de commandes isolé vous permet de déterminer les fonctionnalités Visual Studio dont vous avez besoin pour interagir avec votre langage spécifique à un domaine et comment cette solution doit s’afficher. Pour plus d’informations sur le shell isolé Visual Studio, consultez [Personnalisation de l’interpréteur de commandes isolé](https://docs.microsoft.com/visualstudio/extensibility/customizing-the-isolated-shell).

Pour définir un shell Visual Studio en tant que cible de déploiement :

1. Dans le projet **DslPackage** , ouvrez **source.extension.TT**.

2. Sous `<SupportedProducts>` Insérer :

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Remplacez *MyIsolatedShell* par le nom de votre package d’interpréteur de commandes isolé.
