---
title: Déploiement du shell VS
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ca497244a806324d9d2315fa1b1b89404838ff3
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444997"
---
# <a name="vs-shell-deployment"></a>Déploiement du shell VS

Une coque isolée vous permet de déterminer quelle fonctionnalité Visual Studio vous devez interagir avec votre langage spécifique au domaine et comment cette solution doit apparaître. Pour plus d’informations sur la coquille isolée Visual Studio, voir [Customizing the Isolated Shell](https://docs.microsoft.com/visualstudio/extensibility/customizing-the-isolated-shell).

Pour définir une shell Visual Studio comme cible de déploiement :

1. Dans le projet **DslPackage,** ouvert **source.extension.tt**.

2. Sous `<SupportedProducts>` insert:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Remplacez *MyIsolatedShell* par le nom de votre paquet de coquillages isolés.
