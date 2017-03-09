---
title: "Configuration d&#39;avertissements en Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "erreurs (Visual Basic), avertissements"
  - "erreurs d'exécution, avertissements"
  - "avertissements, configurer"
ms.assetid: 99cf4781-bd4d-47b4-91b9-217933509f82
caps.latest.revision: 35
caps.handback.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Configuration d&#39;avertissements en Visual Basic
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le compilateur [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] inclut un ensemble d'avertissements sur le code susceptible de provoquer des erreurs d'exécution.  Vous pouvez utiliser ces informations pour écrire un code plus clair, plus rapide, meilleur avec moins de bogues.  Par exemple, le compilateur génère un avertissement lorsque l'utilisateur essaie d'appeler un membre d'une variable objet non assignée, quitte une fonction sans définir la valeur de retour ou exécute un bloc `Try` avec des erreurs dans la logique pour intercepter des exceptions.  
  
 Parfois, le compilateur fournit une logique supplémentaire au nom de l'utilisateur de sorte que ce dernier puisse se concentrer sur la tâche à exécuter, plutôt que sur l'anticipation d'erreurs possibles.  Dans les versions précédentes de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], `Option Strict` était utilisé pour limiter la logique supplémentaire fournie par le compilateur [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  La configuration des avertissements vous permet de limiter cette logique de manière plus granulaire au niveau des avertissements.  
  
 Vous pouvez personnaliser votre projet et désactiver certains avertissements non appropriés pour votre application tout en transformant les autres avertissements en erreurs.  Cette page explique comment activer et désactiver les avertissements.  
  
## Activation et désactivation des avertissements  
 Il existe deux moyens de configurer les avertissements : vous pouvez les configurer à l'aide du **Concepteur de projets** ou utiliser les options du compilateur **\/warnaserror** et **\/nowarn**.  
  
 L'onglet **Compiler** de la page **Concepteur de projets** vous permet d'activer et de désactiver des avertissements.  Activez la case à cocher **Désactiver tous les avertissements** pour désactiver tous les avertissements ; activez **Considérer tous les avertissements comme des erreurs** pour traiter tous les avertissements comme des erreurs.  Certains avertissements peuvent être affichés ou masqués comme erreur ou avertissement dans le tableau affiché.  
  
 Lorsque **Option Strict** a le paramètre **Inactif**, les avertissements relatifs à **Option Strict** ne peuvent pas être traités indépendamment les uns des autres.  Lorsque **Option Strict** a le paramètre **Actif**, les avertissements associés sont traités comme erreurs, quel que soit leur état.  Lorsque **Option Strict** a le paramètre **Personnalisé** en spécifiant `/optionstrict:custom` dans le compilateur de ligne de commande, les avertissements **Option Strict** peuvent être affichés ou masqués de manière indépendante.  
  
 L'option de ligne de commande **\/warnaserror** du compilateur permet également de spécifier si les avertissements sont traités comme des erreurs.  Vous pouvez ajouter une liste séparée par des virgules à cette option pour spécifier quels avertissements doivent être traités comme des erreurs ou des avertissements à l'aide de \+ ou \-.  Le tableau suivant présente en détail les options possibles.  
  
|Option de ligne de commande|Informations fournies|  
|---------------------------------|---------------------------|  
|`/warnaserror+`|Considérer tous les avertissements comme des erreurs|  
|`/warnsaserror`\-|Ne pas traiter les avertissements comme des erreurs.  Il s'agit de la valeur par défaut.|  
|`/warnaserror+:<warning list` `>`|Traiter les avertissements spécifiques comme des erreurs, répertoriés par leur numéro d'ID d'erreur dans une liste séparée par des virgules.|  
|`/warnaserror-:<warning list>`|Ne pas traiter les avertissements spécifiques comme des erreurs, répertoriés par leur numéro d'ID d'erreur dans une liste séparée par des virgules.|  
|`/nowarn`|Ne pas signaler les avertissements.|  
|`/nowarn:<warning list>`|Ne pas signaler les avertissements spécifiés, répertoriés par leur numéro d'ID d'erreur dans une liste séparée par des virgules.|  
  
 La liste d'avertissements contient les numéros d'ID d'erreur des avertissements qui doivent être traités comme des erreurs et peuvent être utilisés avec les options de ligne de commande pour activer et désactiver des avertissements spécifiques.  Si la liste d'avertissements contient un numéro incorrect, une erreur est signalée.  
  
## Exemples  
 Ce tableau d'exemples d'arguments de ligne de commande décrit le rôle de chaque argument.  
  
|Argument|Description|  
|--------------|-----------------|  
|`vbc /warnaserror`|Spécifie que tous les avertissements doivent être traités comme des erreurs.|  
|`vbc /warnaserror:42024`|Spécifie que cet avertissement 42024 doit être traité comme une erreur.|  
|`vbc /warnaserror:42024,42025`|Spécifie que les avertissements 42024 et 42025 doivent être traités comme des erreurs.|  
|`vbc /nowarn`|Spécifie qu'aucun avertissement ne doit être signalé.|  
|`vbc /nowarn:42024`|Spécifie que cet avertissement 42024 ne doit pas être signalé.|  
|`vbc /nowarn:42024,42025`|Spécifie que les avertissements 42024 et 42025 ne doivent pas être signalés.|  
  
## Types d'avertissements  
 La liste suivante est une liste d'avertissements que vous pouvez traiter comme des erreurs.  
  
### Avertissement de conversion implicite  
 Généré pour les instances de conversion implicite.  Elles ne concernent pas les conversions implicites d'un type numérique intrinsèque en une chaîne lors de l'utilisation de l'opérateur `&`.  La valeur par défaut pour les nouveaux projets est désactivée.  
  
 ID : 42016  
  
### Avertissement d'appel de méthode à liaison tardive et de résolution de surcharge  
 Généré pour les instances de liaison tardive.  La valeur par défaut pour les nouveaux projets est désactivée.  
  
 ID : 42017  
  
### Avertissements d'opérandes de type Objet  
 Générées lorsque les opérandes de type `Object` se produisent et créent une erreur avec `Option Strict On`.  La valeur par défaut pour les nouveaux projets est activée.  
  
 ID : 42018 et 42019  
  
### Avertissements Les déclarations requièrent la clause 'As'  
 Générés lorsqu'une déclaration de variable, de fonction ou de propriété n'ayant pas une clause `As` aurait créé une erreur avec `Option Strict On`.  Les variables qui n'ont pas de type qui leur est assigné sont supposées être de type `Object`.  La valeur par défaut pour les nouveaux projets est activée.  
  
 ID : 42020 \(déclaration de variable\), 42021 \(déclaration de fonction\) et 42022 \(déclaration de propriété\).  
  
### Avertissements d'exception de référence null  
 Générés lorsqu'une variable est utilisée avant qu'une valeur ne lui ait été assignée.  La valeur par défaut pour les nouveaux projets est activée.  
  
 ID : 42104, 42030  
  
### Avertissement de variable locale non utilisée  
 Généré lorsqu'une variable locale est déclarée mais jamais référencée.  La valeur par défaut est activée.  
  
 ID : 42024  
  
### Avertissement d'accès de membre partagé via la variable d'instance  
 Généré lorsque l'accès à un membre partagé via une instance peut avoir des effets secondaires, ou lorsque l'accès à un membre partagé via une variable d'instance n'est pas la partie droite d'une expression ou est passé comme un paramètre.  La valeur par défaut pour les nouveaux projets est activée.  
  
 ID : 42025  
  
### Avertissements d'opérateur récursif ou d'accès de propriété  
 Générés lorsque le corps d'une routine utilise la propriété ou l'opérateur dans lequel il est défini.  La valeur par défaut pour les nouveaux projets est activée.  
  
 ID: 42004 \(opérateur\), 42026 \(propriété\)  
  
### Avertissement de fonction ou d'opérateur sans valeur de retour  
 Généré lorsque la fonction ou l'opérateur n'a pas de valeur de retour spécifiée.  Cela inclut l'omission d'un `Set` sur la variable locale implicite portant le même nom que la fonction.  La valeur par défaut pour les nouveaux projets est activée.  
  
 ID: 42105 \(fonction\), 42016 \(opérateur\)  
  
### Avertissement de modificateur Overloads utilisé dans un module  
 Généré lorsque `Overloads` est utilisé dans un `Module`.  La valeur par défaut pour les nouveaux projets est activée.  
  
 ID : 42028  
  
### Avertissements de blocs dupliqués ou superposés  
 Générés lorsqu'un bloc `Catch` n'est jamais atteint en raison de sa relation à d'autres blocs `Catch` qui ont été définis.  La valeur par défaut pour les nouveaux projets est activée.  
  
 ID : 42029, 42031  
  
## Voir aussi  
 [Assistant Exception, boîte de dialogue](../debugger/exception-assistant-dialog-box.md)   
 [Error Types](/dotnet/visual-basic/programming-guide/language-features/error-types)   
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [\/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn)   
 [\/warnaserror](/dotnet/visual-basic/reference/command-line-compiler/warnaserror)   
 [Page Compiler, Concepteur de projets \(Visual Basic\)](../ide/reference/compile-page-project-designer-visual-basic.md)   
 [Avertissements du compilateur désactivés par défaut](/visual-cpp/preprocessor/compiler-warnings-that-are-off-by-default)