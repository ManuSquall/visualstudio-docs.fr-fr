---
title: Implémentation d’un plug-in de contrôle de code source-meilleures pratiques
description: Passez en revue ces détails techniques pour vous aider à implémenter de manière fiable un plug-in de contrôle de code source dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, best practices
- best practices, source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 80a944c077d520d6d9ecac9557179311ecf20281
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893072"
---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>Meilleures pratiques pour l’implémentation d’un plug-in de contrôle de code source
Les détails techniques suivants peuvent vous aider à implémenter de manière fiable un plug-in de contrôle de code source dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="memory-management-issues"></a>Problèmes de gestion de la mémoire
 Dans la plupart des cas, l’environnement de développement intégré (IDE), qui est l’appelant, libère et alloue de la mémoire. Le plug-in de contrôle de code source retourne des chaînes et d’autres éléments dans les mémoires tampons allouées par l’appelant. Les exceptions sont notées dans les descriptions des fonctions spécifiques où elles se produisent.

## <a name="arrays-of-file-names"></a>Tableaux de noms de fichiers
 Lorsqu’un tableau de fichiers est passé, il n’est pas transmis en tant que tableau contigu de noms de fichiers. Il est passé sous la forme d’un tableau de pointeurs vers des noms de fichiers. Par exemple, dans [SccGet](../extensibility/sccget-function.md), les noms de fichiers sont passés par le `lpFileNames` paramètre, où `lpFileNames` est en fait un pointeur vers un `char **` . `lpFileNames`[0] est un pointeur vers le premier nom, `lpFileNames` [1] est un pointeur vers le deuxième nom, et ainsi de suite.

## <a name="large-model"></a>Modèle volumineux
 Tous les pointeurs sont 32 bits, même sur les systèmes d’exploitation 16 bits.

## <a name="fully-qualified-paths"></a>Chemins d’accès complets
 Lorsque des noms de fichiers ou des répertoires sont spécifiés en tant qu’arguments, ils doivent être des chemins d’accès complets ou UNC, sans les barres obliques inverses de fin. Il est de la responsabilité du plug-in de contrôle de code source de les traduire en chemins d’accès relatifs s’il s’agit d’une exigence du système de contrôle de code source sous-jacent.

## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>Spécifiez un chemin d’accès complet pour la DLL inscrite
 L’IDE ne charge plus les dll à partir de chemins d’accès relatifs (par exemple, *.\NewProvider.dll*). Un chemin d’accès complet à la DLL doit être spécifié (par exemple, *C:\Providers\NewProvider.dll*). Cette exigence renforce la sécurité de l’environnement de développement intégré (IDE) en empêchant le chargement de dll de contrôle de code source non autorisées ou usurpées.

## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>Rechercher un plug-in VSSCI existant lors de l’installation du plug-in de contrôle de code source
 Un utilisateur qui envisage d’installer le plug-in de contrôle de code source a peut-être déjà installé un plug-in de contrôle de code source existant sur l’ordinateur. Le programme d’installation (programme d’installation) pour le plug-in que vous créez doit déterminer s’il existe des valeurs pour les clés de Registre appropriées. Si ces clés sont déjà définies, votre programme d’installation doit demander à l’utilisateur s’il doit inscrire votre plug-in en tant que plug-in de contrôle de code source par défaut et remplacer celui qui est déjà installé.

## <a name="error-result-codes-and-reporting"></a>Rapports et codes de résultats d’erreur
 Le `SCC_OK` Code de retour d’une fonction de contrôle de code source indique que l’opération a réussi pour tous les fichiers. Si l’opération échoue, il est prévu de retourner le dernier code d’erreur rencontré.

 La règle pour la création de rapports est que si une erreur se produit dans l’IDE, l’IDE est responsable de la création de rapports. Si une erreur se produit dans le système de contrôle de code source, le plug-in de contrôle de code source est responsable de sa création de rapports. Par exemple, aucun fichier n’est **actuellement sélectionné** est signalé par l’IDE, alors que **ce fichier est déjà extrait** et signalé par le plug-in.

## <a name="the-context-structure"></a>Structure de contexte
 Pendant l’appel à [SccInitialize](../extensibility/sccinitialize-function.md), l’appelant passe le `ppvContext` paramètre, qui est un handle non initialisé à un void. Le plug-in de contrôle de code source peut ignorer ce paramètre ou il peut allouer une structure de n’importe quel type et placer un pointeur vers cette structure dans le pointeur passé. L’IDE ne comprend pas cette structure, mais il passe un pointeur vers cette structure dans chaque autre appel du plug-in. Cela fournit des informations de cache de contexte précieuses au plug-in qu’il peut utiliser pour conserver les informations d’État globales qui persistent entre les appels de fonction sans utiliser de variables globales. Le plug-in est chargé de libérer la structure sur un appel à [SccUninitialize](../extensibility/sccuninitialize-function.md).

 Si le plug-in définit le `SCC_CAP_REENTRANT` bit dans le [SccInitialize](../extensibility/sccinitialize-function.md) (plus précisément, dans le `lpSccCaps` paramètre), plusieurs structures de contexte sont utilisées pour suivre tous les projets ouverts.

## <a name="bitflags-and-other-command-options"></a>Indicateurs et autres options de commande
 Pour chaque commande, telle que [SccGet](../extensibility/sccget-function.md), l’IDE peut spécifier de nombreuses options qui modifient le comportement de la commande.

 L’API prend en charge la définition de certaines options par l’IDE via le `fOptions` paramètre. Ces options sont décrites dans [indicateurs utilisés par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md) avec les commandes qu’elles affectent. En général, il s’agit des options pour lesquelles l’utilisateur n’est pas invité.

 La plupart des options de paramètre configurables par l’utilisateur ne sont pas définies de cette manière, car elles varient considérablement entre les plug-ins de contrôle de code source. Par conséquent, le mécanisme recommandé est un bouton **avancé** . Par exemple, dans la boîte de dialogue **obtenir** , l’IDE affiche uniquement les informations qu’il comprend, mais il affiche également un bouton **avancé** si le plug-in possède des options pour cette commande. Quand l’utilisateur clique sur le bouton **avancé** , l’IDE appelle [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) pour permettre au plug-in de contrôle de code source d’inviter l’utilisateur à fournir des informations, telles que indicateurs ou une date/heure. Le plug-in retourne ces informations dans une structure qui est retransmise au cours de la `SccGet` commande.

## <a name="see-also"></a>Voir aussi
- [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)
- [Créer un plug-in de contrôle de code source](../extensibility/internals/creating-a-source-control-plug-in.md)
