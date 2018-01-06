---
title: "Déploiement de VS Shell | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: "2"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: aeb4ca2153d4c060862d31e53202312f061bf1ef
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="vs-shell-deployment"></a>Déploiement du shell VS
Un shell isolé vous permet de déterminer où Visual Studio fonctionnalités que vous devez interagir avec votre langage spécifique à un domaine et comment cette solution doit s’afficher. Pour plus d’informations sur le shell isolé Visual Studio, consultez [personnalisation le Shell isolé](../extensibility/customizing-the-isolated-shell.md). Vous trouverez plus d’informations sur la façon de personnaliser le shell isolé dans [personnalisation le Shell isolé](http://msdn.microsoft.com/en-us/d75463cd-1155-42e4-8b7a-046ed6becbbf).  
  
### <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Pour définir un interpréteur de commandes Visual Studio en tant que la cible de déploiement  
  
1.  Dans le **DslPackage** projet, ouvrez **source.extension.tt**.  
  
2.  Sous `<SupportedProducts>` insérer :  
  
    ```  
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>  
    ```  
  
     Remplacez *MyIsolatedShell* avec le nom de votre package de shell isolé.