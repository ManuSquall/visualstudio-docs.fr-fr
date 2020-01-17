---
title: Déploiement du shell VS
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99ef0124c06cd6f1a4d24e29b2c02cd0b50a37b0
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115274"
---
# <a name="vs-shell-deployment"></a>Déploiement du shell VS

Un interpréteur de commandes isolé vous permet de déterminer les fonctionnalités Visual Studio dont vous avez besoin pour interagir avec votre langage spécifique à un domaine et comment cette solution doit s’afficher. Pour plus d’informations sur le shell isolé Visual Studio, consultez [Personnalisation de l’interpréteur de commandes isolé](https://vspartner.com/pages/vsshells).

Pour définir un shell Visual Studio en tant que cible de déploiement :

1. Dans le projet **DslPackage** , ouvrez **source.extension.TT**.

2. Sous `<SupportedProducts>` insérer :

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Remplacez *MyIsolatedShell* par le nom de votre package d’interpréteur de commandes isolé.
