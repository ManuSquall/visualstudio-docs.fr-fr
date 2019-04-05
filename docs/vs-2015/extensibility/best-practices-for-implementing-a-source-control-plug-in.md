---
title: Meilleures pratiques pour implémenter un plug-in de contrôle de code Source | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, best practices
- best practices, source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 99166c8bf9a76deaa3805bfd8f5ac6db35e5c0a0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58950025"
---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>Bonnes pratiques pour implémenter un plug-in de contrôle de code source
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les détails techniques suivantes peuvent vous aider à implémenter de manière fiable un plug-in de contrôle de code source [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="memory-management-issues"></a>Problèmes de gestion de mémoire  
 Dans la plupart des cas, l’environnement de développement intégré (IDE), qui est l’appelant, libère et alloue de la mémoire. Le plug-in de contrôle de code source retourne des chaînes et autres éléments dans les mémoires tampons allouées par l’appelant. Exceptions sont notées dans les descriptions des fonctions spécifiques où elles se produisent.  
  
## <a name="arrays-of-file-names"></a>Tableaux de noms de fichiers  
 Lorsqu’un tableau de fichiers est passé, n’est pas passé en tant que tableau contigu de noms de fichiers. Il est transmis en tant que tableau de pointeurs aux noms de fichiers. Par exemple, dans le [SccGet](../extensibility/sccget-function.md), les noms de fichiers sont passés par le `lpFileNames` paramètre, où `lpFileNames` est en fait un pointeur vers un `char **`. `lpFileNames`[0] est un pointeur vers le premier nom `lpFileNames`[1] est un pointeur vers le nom du deuxième et ainsi de suite.  
  
## <a name="large-model"></a>Modèle de grande taille  
 Tous les pointeurs font 32 bits, même sur les systèmes d’exploitation 16 bits.  
  
## <a name="fully-qualified-paths"></a>Chemins qualifiés complets  
 Où les noms de fichiers ou répertoires sont spécifiés en tant qu’arguments, ils doivent être des chemins qualifiés complets ou des chemins d’accès UNC, sans la barre oblique inverse de fin. Il est la responsabilité du contrôle de source de plug-in pour traduire ces chemins d’accès relatif si qui est une spécification pour le système de contrôle source sous-jacent.  
  
## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>Spécifiez un chemin d’accès qualifié complet pour la DLL enregistrée  
 L’IDE ne charge plus DLL à partir de chemins d’accès relatifs (par exemple,.\NewProvider.dll). Un chemin d’accès complet de la DLL doit être spécifié (par exemple, C:\Providers\NewProvider.dll). Cela renforce la sécurité de l’IDE en empêchant le chargement des DLL du contrôle de source non autorisés ou avec emprunt d’identité.  
  
## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>Recherchez un plug-in de VSSCI existant lorsque vous installez votre plug-in de contrôle de code Source  
 Un utilisateur qui a l’intention d’installer votre plug-in de contrôle de code source peut-être déjà un source contrôle existant plug-in installé sur l’ordinateur. Le programme d’installation (programme d’installation) pour le plug-in que vous créez doit déterminer s’il existe des valeurs existantes pour les clés de Registre appropriées. Si ces clés sont déjà définies, le programme d’installation doit demander l’utilisateur à inscrire votre plug-in en tant que le plug-in de contrôle de code source par défaut et remplacer celle qui est déjà installé.  
  
## <a name="error-result-codes-and-reporting"></a>Codes de résultat d’erreur et la création de rapports  
 Le `SCC_OK` renvoyer le code d’une fonction de contrôle de source indique que l’opération a réussi pour tous les fichiers. Si l’opération échoue, il est prévu pour retourner le dernier code d’erreur rencontré.  
  
 La règle de création de rapports est que si une erreur se produit dans l’IDE, l’IDE est responsable de la signaler. Si une erreur se produit dans le système de contrôle source, le plug-in de contrôle de code source est responsable de la signaler. Par exemple, « aucun fichier actuellement sélectionné » serait signalé par l’IDE, tandis que « ce fichier est déjà extrait » serait signalé par le plug-in.  
  
## <a name="the-context-structure"></a>La Structure de contexte  
 Pendant l’appel à la [SccInitialize](../extensibility/sccinitialize-function.md), l’appelant passe le `ppvContext` paramètre, qui est un handle non initialisé à une valeur void. Le plug-in de contrôle de code source peut ignorer ce paramètre, ou elle peut allouer une structure quelconque et placer un pointeur à cette structure dans le pointeur passé. L’IDE ne comprend pas cette structure, mais il passe un pointeur vers cette structure dans chaque autre appel dans le plug-in. Cela fournit des informations de cache d’un contexte précieux pour le plug-in qu’il peut utiliser pour gérer les informations d’état global qui persiste lors des appels de fonction sans utiliser de variables globales. Le plug-in est chargé de libérer la structure dans un appel à la [SccUninitialize](../extensibility/sccuninitialize-function.md).  
  
 Si les jeux de plug-in le `SCC_CAP_REENTRANT` bit dans le [SccInitialize](../extensibility/sccinitialize-function.md) (en particulier, dans le `lpSccCaps` paramètre), plusieurs structures de contexte sont utilisées pour effectuer le suivi de tous les projets qui sont ouverts.  
  
## <a name="bitflags-and-other-command-options"></a>Indicateurs de bits et d’autres Options de commande  
 Pour chaque commande, telles que la [SccGet](../extensibility/sccget-function.md), l’IDE peut spécifier de nombreuses options qui modifient le comportement de la commande.  
  
 L’API prend en charge le paramètre de certaines options par l’IDE via le `fOptions` paramètre. Ces options sont décrites dans [indicateurs de bits utilisés par les commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md) ainsi que les commandes qu’elles affectent. En règle générale, il s’agit d’options pour lequel l’utilisateur ne doit pas être invité.  
  
 Plus les options de paramètre configurable par l’utilisateur ne sont pas définies de cette manière, car ils peuvent varier entre les plug-ins de contrôle de code source. Par conséquent, le mécanisme recommandé est un **avancé** bouton. Par exemple, dans le **obtenir** boîte de dialogue, l’IDE affiche uniquement les informations qu’il comprend, mais elle affiche également une **avancé** bouton si le plug-in a des options de cette commande. Lorsque l’utilisateur clique sur le **avancé** bouton, les appels de l’IDE le [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) pour activer le plug-in pour inviter l’utilisateur pour plus d’informations, telles que les indicateurs de bits ou une date/heure de contrôle de code source. Le plug-in retourne cette information dans une structure qui est retournée pendant la `SccGet` commande.  
  
## <a name="see-also"></a>Voir aussi  
 [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)   
 [Création d’un plug-in de contrôle de code source](../extensibility/internals/creating-a-source-control-plug-in.md)
