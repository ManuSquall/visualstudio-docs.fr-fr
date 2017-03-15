---
title: "Meilleures pratiques pour impl&#233;menter un plug-in de contr&#244;le de code Source | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "contrôle plug-ins de source, meilleures pratiques"
  - "meilleures pratiques, des plug-ins de contrôle de code source"
  - "contrôle de code source (Visual Studio SDK), plug-ins"
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Meilleures pratiques pour impl&#233;menter un plug-in de contr&#244;le de code Source
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les détails techniques suivantes peuvent vous aider à implémenter de manière fiable un plug\-in de contrôle de code source [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Problèmes de gestion de mémoire  
 Dans la plupart des cas, l'environnement de développement intégré \(IDE\), qui est l'appelant, libère et alloue de la mémoire. Le plug\-in de contrôle de code source retourne des chaînes et autres éléments dans les mémoires tampons allouées par l'appelant. Les exceptions sont notées dans les descriptions des fonctions spécifiques où elles se produisent.  
  
## Tableaux de noms de fichiers  
 Lorsqu'un tableau de fichiers est passé, n'est pas passé en tant que tableau contigu de noms de fichiers. Elle est passée comme un tableau de pointeurs aux noms de fichiers. Par exemple, dans le [SccGet](../extensibility/sccget-function.md), les noms de fichiers sont passés par le `lpFileNames` paramètre, où `lpFileNames` est en fait un pointeur vers un `char **`.`lpFileNames`\[0\] est un pointeur vers le premier nom, `lpFileNames`\[1\] est un pointeur vers le nom du deuxième et ainsi de suite.  
  
## Grand modèle  
 Tous les pointeurs font 32 bits, même sur les systèmes d'exploitation 16 bits.  
  
## Chemins d'accès complets  
 Où les noms de fichiers ou répertoires sont spécifiés en tant qu'arguments, ils doivent être des chemins d'accès complets ou des chemins d'accès UNC, sans la barre oblique inverse de fin. Il est la responsabilité du contrôle de source de plug\-in pour traduire ces chemins d'accès relatif si qui est une spécification pour le système de contrôle source sous\-jacent.  
  
## Spécifiez un chemin d'accès complet pour la DLL inscrite  
 L'IDE ne charge plus DLL à partir de chemins d'accès relatifs \(par exemple,.\\NewProvider.dll\). Un chemin d'accès complet de la DLL doit être spécifié \(par exemple, C:\\Providers\\NewProvider.dll\). Cela renforce la sécurité de l'IDE en empêchant le chargement de la DLL du contrôle source non autorisés ou emprunt d'identité.  
  
## Recherchez un plug\-in de VSSCI existant lorsque vous installez votre plug\-in de contrôle de code Source  
 Un utilisateur qui a l'intention d'installer votre plug\-in de contrôle de code source peut déjà qu'un code source contrôle plug\-in installé sur l'ordinateur. Le programme d'installation \(installation\) du plug\-in que vous créez doit déterminer s'il existe des valeurs existantes pour les clés de Registre appropriés. Si ces clés sont déjà définies, le programme d'installation doit demander l'utilisateur à enregistrer votre plug\-in en tant que le plug\-in de contrôle de code source par défaut et remplacer celle qui est déjà installé.  
  
## Codes de résultat d'erreur et la création de rapports  
 Le `SCC_OK` renvoyer le code d'une fonction de contrôle source indique que l'opération a réussi pour tous les fichiers. Si l'opération échoue, il est prévu pour retourner le dernier code d'erreur.  
  
 La règle de création de rapports est que si une erreur se produit dans l'IDE, l'IDE est responsable de la signaler. Si une erreur se produit dans le système de contrôle source, le plug\-in de contrôle de code source est responsable de la signaler. Par exemple, « aucun fichier n'a n'été sélectionné » serait signalé par l'IDE, tandis que « ce fichier est déjà extrait » serait signalé par le plug\-in.  
  
## La Structure de contexte  
 Lors de l'appel à la [SccInitialize](../extensibility/sccinitialize-function.md), l'appelant passe le `ppvContext` paramètre, qui est un handle non initialisé à une valeur vide. Le plug\-in de contrôle de code source peut ignorer ce paramètre, ou elle peut allouer une structure de n'importe quel type et placer un pointeur à cette structure dans le pointeur passé. L'IDE ne comprend pas cette structure, mais il passe un pointeur vers cette structure dans chaque autre appel dans le plug\-in. Fournit des informations de cache de contexte précieuses pour le plug\-in qu'il peut utiliser pour gérer les informations d'état global qui persiste lors des appels de fonction sans utiliser des variables globales. Le plug\-in est chargé de libérer la structure sur un appel à la [SccUninitialize](../extensibility/sccuninitialize-function.md).  
  
 Si le plug\-in définit la `SCC_CAP_REENTRANT` bit dans le [SccInitialize](../extensibility/sccinitialize-function.md) \(en particulier, dans le `lpSccCaps` paramètre\), plusieurs structures de contexte sont utilisées pour effectuer le suivi de tous les projets ouverts.  
  
## Indicateurs de bits et d'autres Options de commande  
 Pour chaque commande, telles que la [SccGet](../extensibility/sccget-function.md), l'IDE peut spécifier plusieurs options qui modifient le comportement de la commande.  
  
 L'API prend en charge le paramètre de certaines options par l'IDE via le `fOptions` paramètre. Ces options sont décrites dans [Indicateurs de bits utilisés par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md) ainsi que les commandes qu'elles affectent. En général, il s'agit d'options pour lesquelles l'utilisateur ne doit pas être invité.  
  
 Plus les options de paramètre configurable par l'utilisateur ne sont pas définies de cette manière, car ils peuvent varier parmi les plug\-ins de contrôle de code source. Par conséquent, le mécanisme recommandé est un **Avancé** bouton. Par exemple, dans le **obtenir** boîte de dialogue, l'IDE affiche uniquement les informations qu'il comprend, mais elle affiche également une **Avancé** bouton si le plug\-in a des options de cette commande. Lorsque l'utilisateur clique sur le **Avancé** bouton, les appels IDE le [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) pour activer le contrôle de code source du plug\-in pour inviter l'utilisateur pour plus d'informations, telles que les indicateurs de bits ou une date\/heure. Le plug\-in renvoie ces informations dans une structure qui est retournée pendant le `SccGet` commande.  
  
## Voir aussi  
 [Plug\-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)   
 [Création d'un contrôle de Source de plug\-in](../extensibility/internals/creating-a-source-control-plug-in.md)