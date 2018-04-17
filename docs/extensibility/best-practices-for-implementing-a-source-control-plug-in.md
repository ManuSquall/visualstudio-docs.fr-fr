---
title: Meilleures pratiques pour l’implémentation d’un plug-in de contrôle de code Source | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, best practices
- best practices, source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d5e9972b28d435f5cba360b2328ecdd6d18eb52e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>Meilleures pratiques pour implémenter un plug-in de contrôle de code Source
Les détails techniques suivantes peuvent vous aider à implémenter de manière fiable un plug-in de contrôle de code source [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="memory-management-issues"></a>Problèmes de gestion de mémoire  
 Dans la plupart des cas, l’environnement de développement intégré (IDE), qui est l’appelant, libère et alloue de la mémoire. Le plug-in de contrôle de code source retourne des chaînes et autres éléments dans les mémoires tampons allouées par l’appelant. Les exceptions sont indiquées dans les descriptions des fonctions spécifiques où elles se produisent.  
  
## <a name="arrays-of-file-names"></a>Tableaux de noms de fichiers  
 Quand un tableau de fichiers est passé, n’est pas passé en tant que tableau contigu de noms de fichiers. Il est passé en tant que tableau de pointeurs à des noms de fichier. Par exemple, dans le [SccGet](../extensibility/sccget-function.md), les noms de fichiers sont passés par le `lpFileNames` paramètre, où `lpFileNames` est en fait un pointeur vers un `char **`. `lpFileNames`[0] est un pointeur vers le premier nom, `lpFileNames`[1] est un pointeur vers le nom du second et ainsi de suite.  
  
## <a name="large-model"></a>Modèle volumineux  
 Tous les pointeurs font 32 bits, même sur des systèmes d’exploitation 16 bits.  
  
## <a name="fully-qualified-paths"></a>Chemins d’accès complets  
 Où les noms de fichiers ou répertoires sont spécifiés en tant qu’arguments, ils doivent être des chemins d’accès complets ou UNC, sans la barre oblique inverse de fin. Il incombe de contrôle de source de plug-in pour traduire ces chemins d’accès relatif si qui est une spécification pour le système de contrôle source sous-jacent.  
  
## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>Spécifiez un chemin d’accès qualifié complet pour la DLL inscrite  
 L’IDE ne charge plus DLL à partir de chemins d’accès relatifs (par exemple,.\NewProvider.dll). Un chemin d’accès complet de la DLL doit être spécifié (par exemple, C:\Providers\NewProvider.dll). Cela renforce la sécurité de l’IDE en empêchant le chargement de la DLL du contrôle source non autorisé ou avec emprunt d’identité.  
  
## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>Recherchez un plug-in de VSSCI existant lorsque vous installez votre plug-in de contrôle de code Source  
 Un utilisateur qui a l’intention d’installer votre plug-in de contrôle de code source peut-être déjà un source contrôle existant plug-in installé sur l’ordinateur. Le programme d’installation (programme d’installation) pour le plug-in que vous créez doit déterminer s’il existe des valeurs existantes pour les clés de Registre appropriées. Si ces clés sont déjà définis, le programme d’installation doit demander l’utilisateur à enregistrer votre plug-in en tant que le plug-in de contrôle de code source par défaut et remplacer celle qui est déjà installé.  
  
## <a name="error-result-codes-and-reporting"></a>Codes de résultat d’erreur et la création de rapports  
 Le `SCC_OK` retourner le code d’une fonction de contrôle de source indique que l’opération a réussi pour tous les fichiers. Si l’opération échoue, il est prévu pour retourner le dernier code d’erreur.  
  
 La règle de création de rapports est que si une erreur se produit dans l’IDE, l’IDE est responsable de la signaler. Si une erreur se produit dans le système de contrôle de code source, le plug-in de contrôle de code source est responsable de la signaler. Par exemple, « aucuns fichiers ne sont actuellement sélectionnés » sont signalé par l’IDE, alors que « ce fichier est déjà extrait » serait signalé par le plug-in.  
  
## <a name="the-context-structure"></a>La Structure de contexte  
 Lors de l’appel à la [SccInitialize](../extensibility/sccinitialize-function.md), l’appelant passe le `ppvContext` paramètre, qui est un handle non initialisé à une valeur vide. Le plug-in de contrôle de code source peut ignorer ce paramètre, ou elle peut allouer une structure de n’importe quel type et placer un pointeur à cette structure dans le pointeur passé. L’IDE ne comprend pas de cette structure, mais il passe un pointeur vers cette structure dans chaque autre appel dans le plug-in. Fournit des informations de cache de contexte importantes pour le plug-in qu’il peut utiliser pour gérer les informations d’état global qui persiste lors des appels de fonction sans utiliser des variables globales. Le plug-in est responsable de la libération de la structure d’un appel à la [SccUninitialize](../extensibility/sccuninitialize-function.md).  
  
 Si le plug-in définit le `SCC_CAP_REENTRANT` bit dans le [SccInitialize](../extensibility/sccinitialize-function.md) (en particulier, dans le `lpSccCaps` paramètre), plusieurs structures de contexte sont utilisées pour effectuer le suivi de tous les projets qui sont ouverts.  
  
## <a name="bitflags-and-other-command-options"></a>Indicateurs de bits et d’autres Options de commande  
 Pour chaque commande, telles que la [SccGet](../extensibility/sccget-function.md), l’IDE peut spécifier plusieurs options qui modifient le comportement de la commande.  
  
 L’API prend en charge le paramètre de certaines options par l’IDE via le `fOptions` paramètre. Ces options sont décrites dans [indicateurs de bits utilisés par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md) ainsi que les commandes qu’elles affectent. En règle générale, il s’agit d’options pour laquelle l’utilisateur ne doit pas être invité.  
  
 Plus les options de paramètre configurable par l’utilisateur ne sont pas définies de cette manière, car ils peuvent varier parmi les plug-ins de contrôle de code source. Par conséquent, le mécanisme recommandé est un **avancé** bouton. Par exemple, dans le **obtenir** boîte de dialogue, l’IDE affiche uniquement les informations qu’il comprend, mais elle affiche également une **avancé** bouton si le plug-in a des options de cette commande. Lorsque l’utilisateur clique sur le **avancé** bouton, les appels de l’IDE le [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) pour activer le contrôle de source de plug-in pour inviter l’utilisateur pour plus d’informations, telles que les indicateurs de bits ou une date/heure. Le plug-in retourne cette information dans une structure qui est retournée pendant le `SccGet` commande.  
  
## <a name="see-also"></a>Voir aussi  
 [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)   
 [Création d’un plug-in de contrôle de code source](../extensibility/internals/creating-a-source-control-plug-in.md)