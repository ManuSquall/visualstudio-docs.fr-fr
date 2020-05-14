---
title: Meilleures pratiques pour la mise en œuvre d’un plug-in de contrôle des sources (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, best practices
- best practices, source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 68491f22d63ae3ebb664b7c22188a661dccbf39a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740057"
---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>Meilleures pratiques pour la mise en œuvre d’un plug-in de contrôle des sources
Les détails techniques suivants peuvent vous aider à implémenter de manière fiable un plug-in de contrôle [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]source.

## <a name="memory-management-issues"></a>Problèmes de gestion de la mémoire
 Dans la plupart des cas, l’environnement de développement intégré (IDE), qui est l’appelant, libère et alloue la mémoire. Le plug-in de contrôle source renvoie les chaînes et autres éléments dans les tampons alloués par l’appelant. Des exceptions sont notées dans les descriptions de fonctions spécifiques où elles se produisent.

## <a name="arrays-of-file-names"></a>Arrays de noms de fichiers
 Lorsqu’un tableau de fichiers est adopté, il n’est pas adopté comme un tableau contigus de noms de fichiers. Il est adopté comme un tableau de pointeurs pour classer les noms. Par exemple, dans le [SccGet](../extensibility/sccget-function.md), les `lpFileNames` noms `lpFileNames` de fichier sont `char **`passés par le paramètre, où est en fait un pointeur à un . `lpFileNames`[0] est un pointeur `lpFileNames`du prénom, [1] est un pointeur au deuxième nom, et ainsi de suite.

## <a name="large-model"></a>Grand modèle
 Tous les pointeurs sont 32 bits, même sur les systèmes d’exploitation 16 bits.

## <a name="fully-qualified-paths"></a>Chemins entièrement qualifiés
 Lorsque les noms de fichiers ou les répertoires sont spécifiés comme arguments, ils doivent être des chemins entièrement qualifiés ou des voies unC, sans les contredations de fin. Il incombe au plug-in de contrôle source de traduire ces voies à des trajectoires relatives si c’est une exigence du système de contrôle des sources sous-jacent.

## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>Spécifier un chemin entièrement qualifié pour le DLL enregistré
 L’IDE ne charge plus les DLL à partir de chemins relatifs (par exemple, *.- NewProvider.dll*). Un chemin complet de la DLL doit être spécifié (par exemple, *C: 'Providers’NewProvider.dll*). Cette exigence renforce la sécurité de l’IDE en empêchant le chargement de DLL de contrôle source non autorisé ou usurpé par l’identité.

## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>Vérifiez s’il y a un plug-in VSSCI existant lorsque vous installez votre plug-in de contrôle source
 Un utilisateur qui prévoit d’installer votre plug-in de contrôle source peut déjà avoir un plug-in de contrôle source existant installé sur l’ordinateur. Le programme d’installation (configuration) pour le plug-in que vous créez doit déterminer s’il existe des valeurs existantes pour les clés de registre pertinentes. Si ces clés sont déjà définies, votre programme d’installation devrait demander à l’utilisateur s’il y a un plug-in de contrôle par défaut et remplacer celui qui est déjà installé.

## <a name="error-result-codes-and-reporting"></a>Codes de résultat d’erreur et rapports
 Le `SCC_OK` code de retour d’une fonction de contrôle source indique que l’opération a réussi pour tous les fichiers. Si l’opération échoue, on s’attend à ce qu’elle renvoie le dernier code d’erreur rencontré.

 La règle de déclaration est que si une erreur se produit dans l’IDE, l’IDE est responsable de la signaler. Si une erreur se produit dans le système de contrôle source, le plug-in de contrôle source est responsable de la signaler. Par exemple, **aucun fichier actuellement sélectionné ne** serait signalé par l’IDE, alors que ce fichier est déjà **vérifié** serait signalé par le plug-in.

## <a name="the-context-structure"></a>La structure contextuelle
 Lors de l’appel à la [SccInitialize](../extensibility/sccinitialize-function.md), l’appelant passe le `ppvContext` paramètre, qui est une poignée uninitialisée à un vide. Le plug-in de contrôle source peut ignorer ce paramètre ou il peut allouer une structure de toute sorte et mettre un pointeur à cette structure dans le pointeur passé. L’IDE ne comprend pas cette structure, mais il passe un pointeur à cette structure dans tous les autres appels dans le plug-in. Cela fournit des informations précieuses cache contextuelle au plug-in qu’il peut utiliser pour maintenir des informations étatiques mondiales qui persistent à travers les appels de fonction sans utiliser de variables globales. Le plug-in est responsable de libérer la structure sur un appel à la [SccUninitialize](../extensibility/sccuninitialize-function.md).

 Si le plug-in `SCC_CAP_REENTRANT` place le bit dans le [SccInitialize](../extensibility/sccinitialize-function.md) (en particulier, dans le `lpSccCaps` paramètre), plusieurs structures contextuelles sont utilisées pour suivre tous les projets qui sont ouverts.

## <a name="bitflags-and-other-command-options"></a>Bitflags et autres options de commande
 Pour chaque commande, comme le [SccGet](../extensibility/sccget-function.md), l’IDE peut spécifier de nombreuses options qui modifient le comportement de la commande.

 L’API prend en charge le réglage `fOptions` de certaines options par l’IDE à travers le paramètre. Ces options sont décrites dans [Bitflags utilisés par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md) ainsi que les commandes qu’elles affectent. En général, ce sont des options pour lesquelles l’utilisateur ne serait pas invité.

 La plupart des options de réglage configurables par les utilisateurs ne sont pas définies de cette manière, car elles varient considérablement d’un plug-in de contrôle source. Par conséquent, le mécanisme recommandé est un bouton **Avancé.** Par exemple, dans la boîte de dialogue **Get,** l’IDE affiche uniquement les informations qu’il comprend, mais il affiche également un bouton **Advanced** si le plug-in a des options pour cette commande. Lorsque l’utilisateur clique sur le bouton **Advanced,** l’IDE appelle les [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) pour activer le plug-in de contrôle source pour inciter l’utilisateur à obtenir des informations, telles que des bitflags ou une date/heure. Le plug-in renvoie cette information dans une `SccGet` structure qui est re passée pendant la commande.

## <a name="see-also"></a>Voir aussi
- [Plug-ins de contrôle des sources](../extensibility/source-control-plug-ins.md)
- [Créer un plug-in de contrôle source](../extensibility/internals/creating-a-source-control-plug-in.md)
