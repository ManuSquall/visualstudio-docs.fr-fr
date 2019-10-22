---
title: Déploiement de l’interpréteur de commandes VS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a42ec6a762655589bfd589ae9dc0354e3a7d1cb5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659306"
---
# <a name="vs-shell-deployment"></a>Déploiement du shell VS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un interpréteur de commandes isolé vous permet de déterminer les fonctionnalités Visual Studio dont vous avez besoin pour interagir avec votre langage spécifique à un domaine et comment cette solution doit s’afficher. Pour plus d’informations sur le shell isolé Visual Studio, consultez [Personnalisation de l’interpréteur de commandes isolé](../extensibility/customizing-the-isolated-shell.md). Vous trouverez plus d’informations sur la personnalisation de l’interpréteur de commandes isolé dans [Personnalisation de l’interpréteur](https://msdn.microsoft.com/d75463cd-1155-42e4-8b7a-046ed6becbbf)de commandes isolé.

### <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Pour définir un shell Visual Studio en tant que cible de déploiement

1. Dans le projet **DslPackage** , ouvrez **source.extension.TT**.

2. Sous `<SupportedProducts>` insérer :

    ```
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
    ```

     Remplacez *MyIsolatedShell* par le nom de votre package d’interpréteur de commandes isolé.
