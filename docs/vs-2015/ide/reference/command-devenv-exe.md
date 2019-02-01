---
title: -Command (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /command switch
- /command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 317103b514a04ca149940513e4e70c2799037e62
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54775899"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Exécute la commande spécifiée après le lancement de l’environnement de développement intégré (IDE) [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
devenv /command CommandName  
```  
  
## <a name="arguments"></a>Arguments  
 `CommandName`  
 Obligatoire. Nom complet d’une commande [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ou de son alias, entouré de guillemets doubles. Pour plus d’informations sur la syntaxe des commandes et des alias, consultez [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md).  
  
## <a name="remarks"></a>Notes  
 Une fois le démarrage terminé, l’IDE exécute la commande nommée. Si vous utilisez ce commutateur, l’IDE n’affiche pas la page de démarrage de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] lors du démarrage.  
  
 Si un complément expose une commande, vous pouvez utiliser ce commutateur pour lancer le complément à partir de la ligne de commande. Pour plus d'informations, voir [Procédure : Contrôler des compléments avec le Gestionnaire de compléments](http://msdn.microsoft.com/library/4f60444a-cb48-4cdb-8df4-941f6419aeeb).  
  
## <a name="example"></a>Exemple  
 Cet exemple lance [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] et exécute automatiquement la macro Open Favorite Files.  
  
```  
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commutateurs de la ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
