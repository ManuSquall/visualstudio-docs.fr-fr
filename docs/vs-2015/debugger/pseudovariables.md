---
title: Les pseudo-variables | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Watch window, pseudovariables
- debugging [Visual Studio], pseudovariables
- pseudovariables
ms.assetid: fae84f68-2138-4144-9bd4-c9e271b6182a
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 79d2f47acfbd5a4b6adf6d5f679fb3b514679dab
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789497"
---
# <a name="pseudovariables"></a>Pseudo-variables
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les pseudo-variables sont des termes utilisés pour afficher certaines informations dans une fenêtre de variable ou la **Espion express** boîte de dialogue. Vous pouvez entrer une pseudo-variable de la même façon qu'une variable normale. Toutefois, les pseudo-variables ne sont pas des variables et ne correspondent pas à des noms de variable de votre programme.  
  
## <a name="example"></a>Exemple  
 Supposez que vous écrivez une application en code natif et que vous voulez afficher le nombre de handles alloués à votre application. Dans le **espion** fenêtre, vous pouvez entrer la pseudo-variable suivante dans le **nom** colonne, puis appuyez sur ENTRÉE pour l’évaluer :  
  
```  
$handles  
```  
  
 En code natif, vous pouvez utiliser les pseudo-variables indiquées dans le tableau suivant :  
  
|Pseudo-variable|Fonction|  
|--------------------|--------------|  
|`$err`|Affiche la dernière valeur d'erreur définie avec la fonction SetLastError. La valeur affichée représente la valeur retournée par la fonction GetLastError.<br /><br /> Utilisez `$err,hr` pour afficher cette valeur sous une forme décodée. Par exemple, si la dernière erreur est 3, `$err,hr` affiche `ERROR_PATH_NOT_FOUND : The system cannot find the path specified.`|  
|`$handles`|Affiche le nombre de handles alloués à votre application.|  
|`$vframe`|Affiche l'adresse du frame de pile actuel.|  
|`$tid`|Affiche l'ID du thread actuel.|  
|`$env`|Affiche le bloc environnement de l'explorateur de chaînes.|  
|`$cmdline`|Affiche la chaîne de ligne de commande qui a lancé le programme.|  
|`$pid`|Affiche l'ID du processus.|  
|`$` *RegisterName*<br /><br /> ou<br /><br /> `@` *RegisterName*|Affiche le contenu du Registre *registername*.<br /><br /> En règle générale, vous pouvez afficher le contenu du registre en entrant simplement son nom. Vous n'avez besoin d'utiliser cette syntaxe que lorsque le nom de registre surcharge le nom d'une variable. Si le nom de registre est le même que celui d'une variable dans la portée actuelle, le débogueur interprète le nom comme étant celui de la variable. C’est quand `$` *registername* ou `@` *registername* s’avère pratique.|  
|`$clk`|Affiche le temps en cycles d'horloge.|  
|`$user`|Affiche une structure avec les informations du compte qui exécute l'application. Pour des raisons de sécurité, les informations de mot de passe ne sont pas affichées.|  
|`$exceptionstack`|Affiche l'arborescence des appels de procédure de l'exception Windows Runtime actuelle. `$ exceptionstack` ne fonctionne que dans les applications Windows Store s'exécutant dans Windows 8.1 ou version ultérieure. `$ exceptionstack` n'est pas pris en charge pour les exceptions C++ et SHE|  
|`$ReturnValue`|Affiche la valeur de retour d'une méthode .NET Framework. Consultez [Examine les valeurs de retour d’appels de méthode](http://msdn.microsoft.com/library/e3245b37-8e2e-4200-ba84-133726e95f1f)|  
  
 En C# et Visual Basic, vous pouvez utiliser les pseudo-variables indiquées dans le tableau suivant :  
  
|Pseudo-variable|Fonction|  
|--------------------|--------------|  
|`$exception`|Affiche des informations sur la dernière exception. Si aucune exception ne s'est produite, l'évaluation de `$exception` affiche un message d'erreur.<br /><br /> Dans Visual c# uniquement, lorsque l’Assistant Exception est désactivé, `$exception` est automatiquement ajouté à la **variables locales** fenêtre lorsqu’une exception se produit.|  
|`$user`|Affiche une structure avec les informations du compte qui exécute l'application. Pour des raisons de sécurité, les informations de mot de passe ne sont pas affichées.|  
  
 En Visual Basic, vous pouvez utiliser les pseudo-variables indiquées dans le tableau suivant :  
  
|Pseudo-variable|Fonction|  
|--------------------|--------------|  
|`$delete` ou `$$delete`|Supprime une variable implicite qui a été créée dans le **immédiat** fenêtre. La syntaxe est `$delete,` *variable* ou`$delete,` *variable*`.`|  
|`$objectids` ou `$listobjectids`|Affiche tous les ID d'objet actifs en tant qu'enfants de l'expression spécifiée. La syntaxe est `$objectid,` *expression* ou`$listobjectids,` *expression*`.`|  
|`$` *N* `#`|Affiche l’objet avec l’ID d’objet égal à *N*.|  
|`$dynamic`|Affiche les spéciale **affichage dynamique** nœud pour un objet qui implémente le `IDynamicMetaObjectProvider`. Interface. La syntaxe est `$dynamic,` *objet*. Cette fonctionnalité s’applique uniquement au code utilisant .NET Framework version 4. Consultez [affichage dynamique](http://msdn.microsoft.com/library/4c851b17-2c12-46a0-9828-eb6ea6f5c563).|  
  
## <a name="see-also"></a>Voir aussi  
 [Espion et Espion express Windows](../debugger/watch-and-quickwatch-windows.md)   
 [Variable Windows](http://msdn.microsoft.com/library/ce0a67f6-2502-4b7a-ba45-cc32f8aeba3e)





