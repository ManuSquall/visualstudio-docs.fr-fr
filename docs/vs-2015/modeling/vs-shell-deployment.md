---
title: Déploiement du Shell VS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5bfe88d7e7d742eb67273d307c3a8e72e9a85833
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704049"
---
# <a name="vs-shell-deployment"></a>Déploiement du shell VS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un interpréteur de commandes isolé vous permet de déterminer où Visual Studio des fonctionnalités que vous avez besoin interagir avec votre langage spécifique à un domaine et la manière dont cette solution doit apparaître. Pour plus d’informations sur le shell isolé Visual Studio, consultez [personnalisation du Shell isolé](../extensibility/customizing-the-isolated-shell.md). Vous trouverez plus d’informations sur la personnalisation du shell isolé dans [personnalisation du Shell isolé](https://msdn.microsoft.com/d75463cd-1155-42e4-8b7a-046ed6becbbf).  
  
### <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Pour définir un Shell Visual Studio comme cible de déploiement  
  
1. Dans le **DslPackage** projet, ouvrez **source.extension.tt**.  
  
2. Sous `<SupportedProducts>` insérer :  
  
    ```  
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>  
    ```  
  
     Remplacez *MyIsolatedShell* avec le nom de votre package de shell isolé.
