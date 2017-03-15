---
title: "Modification de l’interpréteur de commandes isolé à l’aide de la. Fichier de Pkgundef | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode, .pkgundef file
ms.assetid: 9cee2a20-f8ac-4d9d-aef9-068fcd9f27a4
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: b49f3c5a39e82e0385aab12ef7042a6845b12664
ms.lasthandoff: 02/22/2017

---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>Modification de l’interpréteur de commandes isolé à l’aide de la. Fichier de Pkgundef
Vous pouvez modifier le fichier .pkgundef pour exclure les entrées de Registre spécifiée à partir d’une application de shell isolé. En règle générale, lors du premier que démarrage d’une application sur un ordinateur, le shell Visual Studio copie les entrées de Registre Visual Studio existantes pour la clé de Registre racine pour l’application. Cela inclut toutes les références aux packages VS actuellement installées.  
  
 Pour exclure une entrée de Registre spécifique à partir d’une application de shell isolé, ajoutez dans le fichier .pkgundef de la clé de package suivie de l’entrée. Les clés et les entrées sont représentées comme dans le fichier .pkgdef. Autrement dit, en tant que [$$RootKey] ou [$RootKey$\\*sous-clé*] et «*entrée*» =*valeur*, où *sous-clé* est la sous-clé à affecter, *entrée* est l’entrée à supprimer, et *valeur* est `""` ou `dword:00000000`.  
  
 Pour exclure plusieurs entrées à partir d’une clé de Registre, énumérez la clé une fois, suivi d’une ligne pour chaque entrée à exclure.  
  
 Pour exclure une clé de Registre entier à partir d’une application de shell isolé, ajoutez la clé dans le fichier .pkgundef, mais ne spécifiez pas les entrées de Registre pour cette clé.  
  
 Vous pouvez ajouter des commentaires dans le fichier .pkgundef. Un commentaire sur une ligne doit avoir deux barres obliques que les deux premiers caractères.  
  
 Par exemple, pour supprimer la **se connecter à la base de données** et **se connecter au serveur r** des commandes sur le **outils** menu, vous pouvez supprimer la ligne :  
  
```  
[$RootKey$\Packages\{8D8529D3-625D-4496-8354-3DAD630ECC1B}]  
```  
  
 et ajoutez la ligne :  
  
```  
[$RootKey$\Packages\{198E76C1-34C0-424D-9957-B3EBD80265FB}]  
```  
  
 fichier .pkgundef de l’application.  
  
## <a name="see-also"></a>Voir aussi  
 [GUID du package de fonctionnalités de Visual Studio](../extensibility/package-guids-of-visual-studio-features.md)   
 [Personnalisation de l’interpréteur de commandes isolé](../extensibility/customizing-the-isolated-shell.md)
