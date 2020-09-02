---
title: VSPerfASPNetCmd | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- profiling tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
ms.assetid: f9e9f895-57bb-41e8-8bd1-cdaa738ec220
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b6ddadc15a5e0d53535b82d87aadd31fec65adaf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85330483"
---
# <a name="vsperfaspnetcmd"></a>VSPerfASPNetCmd
L’outil en ligne de commande **VSPerfASPNetCmd.exe** vous permet de profiler des sites web ASP.NET sans devoir définir des variables d’environnement ou redémarrer votre ordinateur. Utilisez **VSPerfASPNetCmd.exe** à la place de [VSPerfCmd](../profiling/vsperfcmd.md) quand vous profilez des sites web ASP.NET et que vous n’avez pas besoin des fonctionnalités supplémentaires fournies par **VSPerfCmd**. Pour plus d’informations sur **VSPerfASPNETCmd**, consultez [profilage de site Web rapide avec VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md). **VSPerfASPNETCmd** est l’outil en ligne de commande par défaut à utiliser lorsque vous utilisez le profileur autonome pour profiler un site Web ASP.net.

## <a name="syntax"></a>Syntaxe
 **vsperfaspnetcmd** [/*Options*] *site_web*

## <a name="options"></a>Options

|Option|Description|
|------------|-----------------|
|**/Sample** ou   **/s**|Profile un site web à l’aide de la méthode par échantillonnage. **/Sample** est la méthode par défaut. Vous ne pouvez pas utiliser /Sample avec **/Trace**.|
|**/Trace** ou   **/t**|Profile un site web à l’aide de la méthode par instrumentation. Vous ne pouvez pas utiliser /Trace avec **/Sample**.|
|**/Memory**[**:** `Type` ] ou **/m**[**:**{**a**&#124;**l**}]|Profile l’allocation de mémoire et éventuellement les durées de vie des objets (garbage collection). Vous pouvez utiliser **/Memory** avec la méthode par échantillonnage ou par instrumentation.<br /><br /> *Type* peut avoir l’une des valeurs suivantes :<br /><br /> -   **allocation** (ou **a**) collecte uniquement les données d’allocation de mémoire.<br />-   **lifetime** (ou **l**) collecte les données d’allocation de la mémoire et de durée de vie des objets.<br /><br /> La valeur par défaut de `Type` est **allocation**.|
|**/Tip** ou   **/i**|Ajoute une requête ASP.NET détaillée et des informations d’appel ADO.NET aux données de profilage. Vous pouvez utiliser **/Tip** avec la méthode par échantillonnage ou par instrumentation, ainsi qu’avec l’option **/Memory**.|
|**/Output:** `File` ou   **/o:**`File`|Spécifie le chemin d’accès et le nom de fichier des données de profilage (.* vsp*).|
|**/NoWait** ou   **/n**|Retourne immédiatement l’invite de commandes pour que des commandes supplémentaires puissent être utilisées dans la fenêtre d’invite de commandes. Vous devez taper **VSPerfASPNETCmd /Shutdown** sur une ligne de commande séparée pour désactiver le profilage.|
|**/PackSymbols**[:{**on**&#124;**off**} ou   **/p**[:{**on**&#124;**off**}|Incorpore des symboles (noms de fonction et de paramètre, etc.) dans le fichier de données de profilage (.*vsp*).|
|**/Shutdown:** `Website` ou   **/d:**`Website`|Désactive le profilage. Utilisez-la comme unique option sur une ligne de commande après avoir utilisé l’option **/NoWait** pour démarrer le profilage, ou si le profileur se ferme de façon inattendue. Spécifiez la même URL que celle utilisée dans la commande **VSPerfASPNETCmd** d’origine.|
|`Website`|URL du site web à profiler.|

## <a name="see-also"></a>Voir aussi
- [Profilage de site Web rapide avec VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)
- [Profiler des applications Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
