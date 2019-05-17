---
title: Modification du Shell isolé à l’aide de le. Fichier de Pkgundef | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .pkgundef file
ms.assetid: 9cee2a20-f8ac-4d9d-aef9-068fcd9f27a4
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: eab02fe900e96ba37c63faae535974788f99ba78
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62538386"
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>Modification du Shell isolé à l’aide de le. Fichier de Pkgundef
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez modifier le fichier .pkgundef pour exclure les entrées de Registre spécifiée à partir d’une application de shell isolé. En règle générale, la première fois qu’une application est démarrée sur un ordinateur, le shell Visual Studio copie les entrées de Registre de Visual Studio existantes dans la clé de Registre racine pour l’application. Cela inclut toutes les références aux VSPackages actuellement installées.  
  
 Pour exclure une entrée de Registre spécifique à partir d’une application de shell isolé, ajoutez au fichier .pkgundef application la clé de package suivie de l’entrée. Entrées et clés sont représentées comme dans le fichier .pkgdef ; Autrement dit, sous la forme [$$RootKey] ou [$RootKey$\\*sous-clé*] et «*entrée*» =*valeur*, où *sous-clé* est la sous-clé à affecter, *entrée* est l’entrée à supprimer, et *valeur* est soit `""` ou `dword:00000000`.  
  
 Pour exclure plusieurs entrées à partir d’une clé de Registre, énumérez pas la clé une fois, suivi d’une ligne pour chaque entrée à exclure.  
  
 Pour exclure une clé de Registre entière à partir d’une application de shell isolé, ajoutez la clé dans le fichier .pkgundef, mais ne spécifiez pas les entrées de Registre pour cette clé.  
  
 Vous pouvez ajouter des commentaires dans le fichier .pkgundef. Un commentaire sur une ligne doit avoir deux barres obliques que les deux premiers caractères.  
  
 Par exemple, pour supprimer le **se connecter à la base de données** et **se connecter au serveur r** commandes sur le **outils** menu, vous pouvez ne pas commenter la ligne :  
  
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
 [Personnalisation du shell isolé](../extensibility/customizing-the-isolated-shell.md)
