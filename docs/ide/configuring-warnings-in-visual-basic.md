---
title: Configuration d'avertissements en Visual Basic
description: Découvrez comment vous pouvez configurer des avertissements dans Visual Basic qui, à son tour, vous aideront à écrire du code plus propre, plus rapide et plus performant, avec moins de bogues.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Basic], warnings
- run-time errors, warnings
- warnings, configuring
ms.assetid: 99cf4781-bd4d-47b4-91b9-217933509f82
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd5239c4fd01aefa247fc63a66af3e872dbecbb6
ms.sourcegitcommit: 66cda27b63c9b55782b1db223a6dbda9f8cabe13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2020
ms.locfileid: "95006404"
---
# <a name="configuring-warnings-in-visual-basic"></a>Configurer les avertissements en Visual Basic

Le compilateur [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] inclut un ensemble d’avertissements concernant le code qui peut provoquer des erreurs d’exécution. Vous pouvez utiliser ces informations pour écrire du code plus clair, plus rapide, de meilleure qualité et avec moins de bogues. Par exemple, le compilateur génère un avertissement si l’utilisateur tente d’appeler un membre d’une variable objet non assignée, de retourner une valeur à partir d’une fonction sans définir la valeur de retour, ou d’exécuter un bloc `Try` contenant des erreurs dans la logique d’interception des exceptions.

Parfois, le compilateur fournit une logique supplémentaire à la place de l’utilisateur pour que celui-ci puisse se concentrer sur la tâche en cours, plutôt que sur l’anticipation d’éventuelles erreurs. Dans les versions précédentes de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], **Option Strict** était utilisé pour limiter la logique supplémentaire fournie par le compilateur [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Vous pouvez choisir de limiter cette logique pour chacun des avertissements.

Il est possible que vous souhaitiez personnaliser votre projet en désactivant certains avertissements non pertinents pour votre application et en transformant certains avertissements en erreurs. Cette page explique comment activer et désactiver chaque avertissement.

## <a name="turning-warnings-off-and-on"></a>Activer et désactiver les avertissements
Il existe deux façons de configurer les avertissements : vous pouvez utiliser le **Concepteur de projet**, ou vous pouvez utiliser les options **/warnaserror** et **/nowarn** du compilateur.

L’onglet **Compiler** de la page **Concepteur de projet** permet d’activer et de désactiver les avertissements. Cochez la case **Désactiver tous les avertissements** pour désactiver tous les avertissements. Cochez la case **Considérer tous les avertissements comme des erreurs** pour traiter tous les avertissements comme des erreurs. Vous pouvez attribuer le statut d’erreur à certains avertissements (et inversement) dans le tableau affiché.

Si **Option Strict** est **Off**, les avertissements relatifs à **Option Strict** ne peuvent pas être traités indépendamment les uns des autres. Si **Option Strict** est **On**, les avertissements qui lui sont associés sont traités comme des erreurs, quel que soit leur état. Si **Option Strict** est défini sur **Custom** en spécifiant `/optionstrict:custom` dans le compilateur de ligne de commande, les avertissements **Option Strict** peuvent être activés ou désactivés indépendamment les uns des autres.

L’option de ligne de commande **/warnaserror** du compilateur peut également être utilisée pour spécifier si les avertissements doivent être traités comme des erreurs. Vous pouvez ajouter une liste séparée par des virgules à cette option pour spécifier que les avertissements doivent être traités comme des erreurs ou des avertissements à l’aide des touches + et -. Le tableau suivant présente les options possibles.

|Option de ligne de commande|Spécifie|
| - |---------------|
|`/warnaserror+`|Considérer tous les avertissements comme des erreurs|
|`/warnsaserror`-|Ne considère pas les avertissements comme des erreurs. Il s’agit de la valeur par défaut.|
|`/warnaserror+:<warning list` `>`|Considère certains avertissements comme des erreurs. Ces avertissements sont répertoriés par numéro d’erreur dans une liste séparée par des virgules.|
|`/warnaserror-:<warning list>`|Ne considère pas certains avertissements comme des erreurs. Ces avertissements sont répertoriés par numéro d’erreur dans une liste séparée par des virgules.|
|`/nowarn`|N’affiche pas d’avertissement.|
|`/nowarn:<warning list>`|N’affiche pas certains avertissements. Ces avertissements sont répertoriés par numéro d’erreur dans une liste séparée par des virgules.|

La liste d’avertissements contient les ID d’erreur des avertissements qui doivent être traités comme des erreurs. Vous pouvez ainsi utiliser les options de ligne de commande pour activer ou désactiver certains avertissements. Si la liste d’avertissements contient un numéro non valide, une erreur est signalée.

## <a name="examples"></a>Exemples
Ce tableau d’exemples d’arguments de ligne de commande décrit le rôle de chaque argument.

|Argument|Description|
|--------------|-----------------|
|`vbc /warnaserror`|Spécifie que tous les avertissements doivent être traités comme des erreurs.|
|`vbc /warnaserror:42024`|Spécifie que l’avertissement 42024 doit être traité comme une erreur.|
|`vbc /warnaserror:42024,42025`|Spécifie que les avertissements 42024 et 42025 doivent être traités comme des erreurs.|
|`vbc /nowarn`|Spécifie qu’aucun avertissement ne doit être signalé.|
|`vbc /nowarn:42024`|Spécifie que l’avertissement 42024 ne doit pas être signalé.|
|`vbc /nowarn:42024,42025`|Spécifie que les avertissements 42024 et 42025 ne doivent pas être signalés.|

## <a name="types-of-warnings"></a>Types d’avertissements
Voici une liste d’avertissements que vous pouvez souhaiter traiter comme des erreurs.

### <a name="implicit-conversion-warning"></a>Conversion implicite
Généré pour les instances de conversion implicite. Cela n’inclut pas les conversions implicites d’un type numérique intrinsèque en une chaîne à l’aide de l’opérateur `&`. Pour les nouveaux projets, la valeur par défaut est Off (désactivé).

ID : 42016

### <a name="late-bound-method-invocation-and-overload-resolution-warning"></a>Appel de méthode à liaison tardive et résolution de surcharge
Généré pour les instances de liaison tardive. Pour les nouveaux projets, la valeur par défaut est Off (désactivé).

ID : 42017

### <a name="operands-of-type-object-warnings"></a>Opérandes de type « Object »
Généré en présence d’opérandes de type `Object`, susceptibles de créer une erreur avec **Option Strict On**. Pour les nouveaux projets, la valeur par défaut est On (activé).

ID : 42018 et 42019

### <a name="declarations-require-as-clause-warnings"></a>Les déclarations nécessitent une clause « As »
Généré lorsqu’une variable, une fonction ou une déclaration de propriété n’ayant pas de clause `As` provoquerait une erreur avec **Option Strict On**. Les variables auxquelles aucun type n’est affecté sont supposées être de type `Object`. Pour les nouveaux projets, la valeur par défaut est On (activé).

ID : 42020 (déclaration de variable), 42021 (déclaration de fonction) et 42022 (déclaration de propriété).

### <a name="possible-null-reference-exception-warnings"></a>Exception de référence Null potentielle
Généré lorsqu’une variable est utilisée avant qu’une valeur ne lui ait été assignée. Pour les nouveaux projets, la valeur par défaut est On (activé).

ID : 42104, 42030

### <a name="unused-local-variable-warning"></a>Variable locale non utilisée
Généré lorsqu’une variable locale est déclarée, mais non référencée. Par défaut, cette option est activée.

ID : 42024

### <a name="access-of-shared-member-through-instance-variable-warning"></a>Accès d’un membre partagé par le biais d’une variable d’instance
Généré lorsque l’accès à un membre partagé via une instance peut avoir des effets secondaires, ou lorsque l’accès à un membre partagé via une variable d’instance n’est pas à droite d’une expression ou est passé comme un paramètre. Pour les nouveaux projets, la valeur par défaut est On (activé).

ID : 42025

### <a name="recursive-operator-or-property-access-warnings"></a>Accès récursif à un opérateur ou à une propriété
Généré lorsque le corps d’une routine utilise le même opérateur ou la même propriété que celui ou celle où il est défini. Pour les nouveaux projets, la valeur par défaut est On (activé).

ID : 42004 (opérateur), 42026 (propriété)

### <a name="function-or-operator-without-return-value-warning"></a>Fonction ou opérateur sans valeur de retour
Généré lorsque la fonction ou l’opérateur n’a pas de valeur de retour. Cela inclut le fait d’omettre un `Set` dans la variable locale implicite portant le même nom que la fonction. Pour les nouveaux projets, la valeur par défaut est On (activé).

ID : 42105 (fonction), 42016 (opérateur)

### <a name="overloads-modifier-used-in-a-module-warning"></a>Modificateur Overloads utilisé dans un module
Généré lorsque `Overloads` est utilisé dans un `Module`. Pour les nouveaux projets, la valeur par défaut est On (activé).

ID : 42028

### <a name="duplicate-or-overlapping-catch-blocks-warnings"></a>Blocs catch dupliqués ou se chevauchant
Généré lorsqu’un bloc `Catch` n’est jamais atteint en raison de sa relation aux autres blocs `Catch` qui ont été définis. Pour les nouveaux projets, la valeur par défaut est On (activé).

ID : 42029, 42031

## <a name="see-also"></a>Voir aussi

- [Types d’erreurs](/dotnet/visual-basic/programming-guide/language-features/error-types)
- [Essayer... Catch... Finally, instruction](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)
- [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn)
- [/warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror)
- [Page compiler, concepteur de projets (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md)
- [Avertissements du compilateur désactivés par défaut](/cpp/preprocessor/compiler-warnings-that-are-off-by-default)
