---
title: Déploiement du shell VS
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e010d2efd8174f2c61d7c97eb63d585f47812ff
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663659"
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