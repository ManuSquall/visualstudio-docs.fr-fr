---
title: Avertissements VSInstr | Microsoft Docs
ms.date: 11/04/2016
description: Découvrez les avertissements émis par l’outil VSInstr.exe et comment vous pouvez utiliser l’option nowarn avec les numéros d’avertissement pour empêcher l’affichage de l’avertissement.
ms.topic: reference
helpviewer_keywords:
- instrumentation, VSInstr tool
- warnings
- VSInstr tool
- warnings, VSInstr tool
- performance tools, VSInstr tool
ms.assetid: 47512bc9-a8e9-4628-883a-d9888edab786
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ed42588f7135b4664b7f65dfcd8c0d979a523aeb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890485"
---
# <a name="vsinstr-warnings"></a>Avertissements VSInstr
Le tableau suivant liste les avertissements émis par l’outil *VSInstr.exe*. Vous pouvez utiliser l’option NOWARN avec les numéros d’avertissement pour empêcher l’affichage de l’avertissement.

|Numéro d’avertissement|Description|
|--------------------|-----------------|
|**VSP1026**|La couverture n’est pas prise en charge sur les bibliothèques qui ne référencent pas MSCorLib. C’est souvent le cas pour les bibliothèques portables.<br /><br />L’option de ligne de commande [/EnableCodeCoverage](../test/vstest-console-options.md) est requise pour .NET Core.|
|**VSP2000**|Erreur interne. Impossible d’obtenir le nom de fichier du module de cet exécutable.|
|**VSP2001**|\<assembly name> est un assembly avec un nom fort. Vous devrez le resigner avant de l’exécuter.<br /><br /> Cet avertissement se produit quand un assembly signé est instrumenté. Vous pouvez utiliser l’outil *sn.exe* pour resigner le fichier binaire ou pour désactiver temporairement l’exigence de nom fort. Pour plus d’informations, consultez [Sn.exe (outil Strong Name Tool)](/dotnet/framework/tools/sn-exe-strong-name-tool).|
|**VSP2002**|Impossible de trouver la fonction \<funcname> dans le fichier \<filename><br /><br /> Cet avertissement se produit si une fonction est introuvable dans le fichier spécifié.|
|**VSP2003**|Impossible de trouver des sauts croisés vers la fonction \<funcname> dans le fichier \<filename> .<br /><br /> Cet avertissement se produit si VSInstr ne peut pas annuler les sauts croisés. Les sauts croisés sont utilisés pour optimiser le code.|
|**VSP2004**|\<funcname>La fonction a été exclue à l’aide du commutateur de ligne de commande exclude mais était requise parce qu’elle contenait un saut croisé.<br /><br /> Cet avertissement se produit quand une fonction exigée pendant le processus d’instrumentation est exclue à l’aide de l’option EXCLUDE. Le profileur inclut automatiquement la fonction exigée.|
|**VSP2005**|Erreur d’instrumentation interne \<error text><br /><br /> Cet avertissement est émis si l’instrumentation ne peut pas être exécutée. Passez en revue le texte d’erreur pour déterminer si l’erreur peut être corrigée.|
|**VSP2006**|Impossible de trouver le fichier PDB pour \<name><br /><br /> Cet avertissement se produit si le fichier PDB n’existe pas dans le chemin de recherche ou ne correspond pas au binaire.|
|**VSP2007**|\<filename> ne contient pas de code instrumenté.<br /><br /> Cet avertissement est émis si les fonctions du fichier binaire ont été toutes exclues ou si le fichier spécifié ne contient que des ressources.|
|**VSP2008**|Impossible d’accéder aux attributs de sécurité à partir de \<name> . Code d’erreur \<code><br /><br /> Cet avertissement se produit si l’utilisateur n’a pas l’autorisation READ_DAC. Durant le processus d’instrumentation, le profileur tente de conserver la liste DACL d’origine du binaire. Étant donné que le binaire d’origine est remplacé par un nouveau binaire, la liste DACL du binaire d’origine doit être copiée et appliquée au nouveau binaire. Cette opération peut échouer si l’utilisateur n’a pas l’accès READ_DAC sur le binaire d’origine.|
|**VSP2009**|Impossible de définir les attributs de sécurité sur \<name> . Code d’erreur \<error number><br /><br /> Cet avertissement se produit si l’utilisateur n’a pas l’autorisation WRITE_DAC. Durant le processus d’instrumentation, le profileur tente de conserver la liste DACL d’origine du binaire. Étant donné que le binaire d’origine est remplacé par un nouveau binaire, la liste DACL du binaire d’origine doit être copiée et appliquée au nouveau binaire. Cette opération peut échouer si l’utilisateur n’a pas l’accès WRITE_DAC sur le nouveau binaire.|
|**VSP2010**|Aucune fonction n’a été sélectionnée pour l’instrumentation en raison des options /INCLUDE ou /EXCLUDE|
|**VSP2011**|La fonction funcspec include/Exclude \<name> ne correspond à aucune fonction|
|**VSP2012**|L’image ne renferme aucun code susceptible d’être instrumenté pour une couverture du code.<br /><br /> Le profileur n’instrumente pas le type de code suivant :<br /><br /> -   Fonctions CRT statiques<br />-   Méthodes managées attribuées avec NonUserCodeAttribute<br />-   Méthodes managées attribuées avec DebuggerHiddenAttribute<br />-   Blocs MASM<br /><br /> Cet avertissement est généré si, après ce filtrage, il ne reste aucun code.|
|**VSP2013**|Vous devez exécuter cette image en tant que processus 32 bits pour pouvoir l’instrumenter. Les indicateurs dans l’en-tête CLR ont été mis à jour pour en tenir compte.<br /><br /> Le profileur modifie le binaire pour que les systèmes d’exploitation 64 bits puissent ouvrir le processus 32 bits dans l’émulateur WOW64. Pour les bibliothèques (DLL), cette opération peut échouer en cas de chargement dans un processus 64 bits existant. Cet avertissement notifie l’utilisateur de la dépendance.|
|**VSP2014**|L’image instrumentée obtenue ne semble pas valide et risque de ne pas s’exécuter.<br /><br /> Ce message se produit quand l’assembly instrumenté final a un en-tête PE non valide.|

## <a name="see-also"></a>Voir aussi
- [VSInstr](../profiling/vsinstr.md)
