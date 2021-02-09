---
title: Déploiement du shell VS
description: Découvrez comment un interpréteur de commandes isolé vous permet de déterminer les fonctionnalités Visual Studio dont vous avez besoin pour interagir avec votre DSL et comment cette solution doit s’afficher.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1293593e71aa57d8e74b9035320b3da5108aba09
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924222"
---
# <a name="vs-shell-deployment"></a>Déploiement du shell VS

Un interpréteur de commandes isolé vous permet de déterminer les fonctionnalités Visual Studio dont vous avez besoin pour interagir avec votre langage spécifique à un domaine et comment cette solution doit s’afficher. Pour plus d’informations sur le shell isolé Visual Studio, consultez [Personnalisation de l’interpréteur de commandes isolé](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/).

Pour définir un shell Visual Studio en tant que cible de déploiement :

1. Dans le projet **DslPackage** , ouvrez **source.extension.TT**.

2. Sous `<SupportedProducts>` Insérer :

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Remplacez *MyIsolatedShell* par le nom de votre package d’interpréteur de commandes isolé.