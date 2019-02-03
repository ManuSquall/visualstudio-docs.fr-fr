---
title: VSPerfASPNetCmd | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
ms.assetid: f9e9f895-57bb-41e8-8bd1-cdaa738ec220
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9cb81f17abd1e7891dc3f78a85d6d1276991f070
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54762989"
---
# <a name="vsperfaspnetcmd"></a>VSPerfASPNetCmd
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’outil en ligne de commande **VSPerfASPNetCmd.exe** vous permet de profiler des sites web ASP.NET sans devoir définir des variables d’environnement ou redémarrer votre ordinateur. Utilisez **VSPerfASPNetCmd.exe** à la place de [VSPerfCmd](../profiling/vsperfcmd.md) lorsque vous profilez des sites web ASP.NET et que vous n’avez pas besoin des fonctionnalités supplémentaires fournies par **VSPerCmd**. Pour plus d’informations sur **VSPerfASPNetCmd**, consultez [Profilage de site web rapide avec VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md). **VSPerfASPNetCmd** est l’outil en ligne de commande à privilégier quand vous utilisez le profileur autonome pour profiler un site web ASP.NET.  
  
## <a name="syntax"></a>Syntaxe  
 **vsperfaspnetcmd** [/*Options*] *site_web*  
  
## <a name="options"></a>Options  
  
|Option|Description|  
|------------|-----------------|  
|**/Sample** ou   **/s**|Profile un site web à l’aide de la méthode par échantillonnage. **/Sample** est la méthode par défaut. Vous ne pouvez pas utiliser /Sample avec **/Trace**.|  
|**/Trace** ou   **/t**|Profile un site web à l’aide de la méthode par instrumentation. Vous ne pouvez pas utiliser /Trace avec **/Sample**.|  
|**/Memory**[**:**`Type`] ou   **/m**[**:**{**a**&#124;**l**}]|Profile l’allocation de mémoire et éventuellement les durées de vie des objets (garbage collection). Vous pouvez utiliser **/Memory** avec la méthode par échantillonnage ou par instrumentation.<br /><br /> *Type* peut avoir l’une des valeurs suivantes :<br /><br /> -   **allocation** (ou **a**) collecte uniquement les données d’allocation de mémoire.<br />-   **lifetime** (ou **l**) collecte les données d’allocation de la mémoire et de durée de vie des objets.<br /><br /> La valeur par défaut de `Type` est **allocation**.|  
|**/Tip** ou   **/i**|Ajoute une requête ASP.NET détaillée et des informations d’appel ADO.NET aux données de profilage. Vous pouvez utiliser **/Tip** avec la méthode par échantillonnage ou par instrumentation, ainsi qu’avec l’option **/Memory**.|  
|**/Output:** `File` ou   **/o:**`File`|Spécifie le chemin et le nom du fichier de données de profilage (.vsp).|  
|**/NoWait** ou   **/n**|Retourne immédiatement l’invite de commandes pour que des commandes supplémentaires puissent être utilisées dans la fenêtre d’invite de commandes. Vous devez taper **VSPerfASPNETCmd /Shutdown** sur une ligne de commande séparée pour désactiver le profilage.|  
|**/PackSymbols**[:{**on**&#124;**off**} ou   **/p**[:{**on**&#124;**off**}|Incorpore des symboles (noms de fonction et de paramètre, etc.) dans le fichier de données de profilage (.vsp).|  
|**/Shutdown:** `Website` ou   **/d:**`Website`|Désactive le profilage. Utilisez-la comme unique option sur une ligne de commande après avoir utilisé l’option **/NoWait** pour démarrer le profilage, ou si le profileur se ferme de façon inattendue. Spécifiez la même URL que celle utilisée dans la commande **VSPerfASPNETCmd** d’origine.|  
|`Website`|URL du site web à profiler.|  
  
## <a name="see-also"></a>Voir aussi  
 [Profilage de site web rapide avec VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
