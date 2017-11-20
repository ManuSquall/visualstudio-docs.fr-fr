---
redirect_url: shell/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file
title: "Modification de l’interpréteur de commandes isolé à l’aide de le. Fichier de Pkgundef | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode, .pkgundef file
ms.assetid: 9cee2a20-f8ac-4d9d-aef9-068fcd9f27a4
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3b4c0f46924c2c828158960a924faa031be0fd14
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>Modification de l’interpréteur de commandes isolé à l’aide de le. Fichier de Pkgundef
Vous pouvez modifier le fichier .pkgundef pour exclure les entrées de Registre spécifiée à partir d’une application de shell isolé. En règle générale, lors du premier que démarrage d’une application sur un ordinateur, le shell Visual Studio copie les entrées de Registre de Visual Studio existantes dans la clé de Registre racine pour l’application. Cela inclut toutes les références aux packages VS actuellement installées.  
  
 Pour exclure une entrée de Registre spécifique à partir d’une application de shell isolé, ajoutez au fichier .pkgundef application l’entrée de suivi de la clé de package. Les clés et les entrées sont représentées comme dans le fichier .pkgdef. Autrement dit, en tant que [$$RootKey] ou [$RootKey$\\*sous-clé*] et «*entrée*» =*valeur*, où *sous-clé* est la sous-clé à affecter, *entrée* est l’entrée à supprimer, et *valeur* est `""` ou `dword:00000000`.  
  
 Pour exclure plusieurs entrées à partir d’une clé de Registre, vous contenter de répertorier la clé une fois, suivi d’une ligne pour chaque entrée à exclure.  
  
 Pour exclure une clé de Registre entier à partir d’une application de shell isolé, ajoutez la clé dans le fichier .pkgundef mais ne spécifiez pas les entrées de Registre pour cette clé.  
  
 Vous pouvez ajouter des commentaires dans le fichier .pkgundef. Un commentaire sur une ligne doit avoir deux barres obliques que les deux premiers caractères.  
  
 Par exemple, pour supprimer la **se connecter à la base de données** et **se connecter au serveur r** des commandes sur le **outils** menu, vous pouvez ne pas commenter la ligne :  
  
```  
[$RootKey$\Packages\{8D8529D3-625D-4496-8354-3DAD630ECC1B}]  
```  
  
 puis, ajoutez la ligne :  
  
```  
[$RootKey$\Packages\{198E76C1-34C0-424D-9957-B3EBD80265FB}]  
```  
  
 fichier .pkgundef de l’application.  
  
## <a name="see-also"></a>Voir aussi  
 [GUID du package de fonctionnalités de Visual Studio](../extensibility/package-guids-of-visual-studio-features.md)   
 [Personnalisation du shell isolé](../extensibility/customizing-the-isolated-shell.md)