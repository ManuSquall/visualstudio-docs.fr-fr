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
ms.openlocfilehash: 6c79a8a0558594e8981959750ebd348b6f9f4d60
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58949750"
---
# <a name="vs-shell-deployment"></a>Déploiement du shell VS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un interpréteur de commandes isolé vous permet de déterminer où Visual Studio des fonctionnalités que vous avez besoin interagir avec votre langage spécifique à un domaine et la manière dont cette solution doit apparaître. Pour plus d’informations sur le shell isolé Visual Studio, consultez [personnalisation du Shell isolé](../extensibility/customizing-the-isolated-shell.md). Vous trouverez plus d’informations sur la personnalisation du shell isolé dans [personnalisation du Shell isolé](http://msdn.microsoft.com/d75463cd-1155-42e4-8b7a-046ed6becbbf).  
  
### <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Pour définir un Shell Visual Studio comme cible de déploiement  
  
1.  Dans le **DslPackage** projet, ouvrez **source.extension.tt**.  
  
2.  Sous `<SupportedProducts>` insérer :  
  
    ```  
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>  
    ```  
  
     Remplacez *MyIsolatedShell* avec le nom de votre package de shell isolé.
