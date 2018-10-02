---
title: Déploiement du Shell VS | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: e1a1bd92d1a0b91aa01d940695cd780f7e63c098
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47508293"
---
# <a name="vs-shell-deployment"></a>Déploiement du shell VS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [déploiement de VS Shell](https://docs.microsoft.com/visualstudio/modeling/vs-shell-deployment).  
  
Un interpréteur de commandes isolé vous permet de déterminer où Visual Studio des fonctionnalités que vous avez besoin interagir avec votre langage spécifique à un domaine et la manière dont cette solution doit apparaître. Pour plus d’informations sur le shell isolé Visual Studio, consultez [personnalisation du Shell isolé](../extensibility/customizing-the-isolated-shell.md). Vous trouverez plus d’informations sur la personnalisation du shell isolé dans [personnalisation du Shell isolé](http://msdn.microsoft.com/en-us/d75463cd-1155-42e4-8b7a-046ed6becbbf).  
  
### <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Pour définir un Shell Visual Studio comme cible de déploiement  
  
1.  Dans le **DslPackage** projet, ouvrez **source.extension.tt**.  
  
2.  Sous `<SupportedProducts>` insérer :  
  
    ```  
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>  
    ```  
  
     Remplacez *MyIsolatedShell* avec le nom de votre package de shell isolé.



