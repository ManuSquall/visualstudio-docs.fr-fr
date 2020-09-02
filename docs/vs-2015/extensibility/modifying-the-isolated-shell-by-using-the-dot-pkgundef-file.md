---
title: Modification de l’interpréteur de commandes isolé à l’aide de. Fichier Pkgundef | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538386"
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>Modification du shell isolé à l’aide du fichier .Pkgundef
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez modifier le fichier. pkgundef pour exclure les entrées de Registre spécifiées d’une application Shell isolée. En règle générale, la première fois qu’une application est démarrée sur un ordinateur, le shell Visual Studio copie les entrées de Registre Visual Studio existantes dans la clé de Registre racine de l’application. Cela comprend toutes les références aux VSPackages actuellement installés.  
  
 Pour exclure une entrée de Registre spécifique d’une application Shell isolée, ajoutez au fichier. pkgundef de l’application la clé de package suivie de l’entrée. Les clés et les entrées sont représentées de la même façon que dans le fichier. pkgdef. autrement dit, As [$RootKey $] ou [$RootKey $ \\ *subkey*] et "*entry*" =*value*, où *subkey* est la sous-clé à affecter, *entry* est l’entrée à supprimer, et *value* est soit `""` ou `dword:00000000` .  
  
 Pour exclure plusieurs entrées d’une clé de Registre, il suffit de répertorier la clé une seule fois, puis une ligne pour chaque entrée à exclure.  
  
 Pour exclure une clé de Registre entière d’une application Shell isolée, ajoutez la clé au fichier. pkgundef de l’application, mais ne spécifiez aucune entrée de Registre pour cette clé.  
  
 Vous pouvez ajouter des commentaires au fichier. pkgundef. Un commentaire sur une seule ligne doit avoir deux barres obliques comme deux premiers caractères.  
  
 Par exemple, pour supprimer les commandes **se connecter à la base de données** et **se connecter aux service r** du menu **Outils** , vous pouvez supprimer les marques de commentaire de la ligne :  
  
```  
[$RootKey$\Packages\{8D8529D3-625D-4496-8354-3DAD630ECC1B}]  
```  
  
 et ajoutez la ligne :  
  
```  
[$RootKey$\Packages\{198E76C1-34C0-424D-9957-B3EBD80265FB}]  
```  
  
 dans le fichier. pkgundef de l’application.  
  
## <a name="see-also"></a>Voir aussi  
 [GUID de package des fonctionnalités Visual Studio](../extensibility/package-guids-of-visual-studio-features.md)   
 [Personnalisation du Shell isolé](../extensibility/customizing-the-isolated-shell.md)
