---
title: Page Compiler, Concepteur de projets (Visual Basic)
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesCompile
helpviewer_keywords:
- compilation, Visual Basic projects
- compilation, options [Visual Basic]
- compilers, Visual Basic options
- compilation, instructions [Visual Basic]
- compiler options, Visual Basic
- Project Designer, Compile page
- Compile page in Project Designer
ms.assetid: b2a80230-906e-4e85-b3e0-fcd9c40426e1
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d9ffdfe4abbef5701cc060171ecbc379ae3a9215
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75570269"
---
# <a name="compile-page-project-designer-visual-basic"></a>Page Compiler, Concepteur de projets (Visual Basic)

La page **Compiler** du Concepteur de projets vous permet de spécifier les instructions de compilation. Vous pouvez également spécifier dans cette page les options avancées du compilateur et les événements pré-build ou post-build.

Pour accéder à la page **Compiler**, choisissez un nœud de projet (pas le nœud **Solution**) dans **l’Explorateur de solutions**. Ensuite, choisissez **Projet**, **Propriétés** dans la barre de menus. Quand le Concepteur de projets apparaît, cliquez sur l’onglet **Compiler**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="configuration-and-platform"></a>Configuration et Plateforme

Les paramètres suivants vous permettent de sélectionner la configuration et la plateforme à afficher ou à modifier.

> [!NOTE]
> Grâce aux configurations de build simplifiées, le système de projet détermine s’il faut générer une version Debug ou Release. Par conséquent, les listes **Configuration** et **Plateforme** ne sont pas affichées.

**Configuration**

Spécifie les paramètres de configuration à afficher ou à modifier. Les paramètres sont **Debug** (valeur par défaut), **Release** ou **Toutes les configurations**. Pour plus d’informations, consultez [Présentation des configurations de build](../../ide/understanding-build-configurations.md) et [Guide pratique pour créer et modifier des configurations](../../ide/how-to-create-and-edit-configurations.md).

**Plateforme**

Spécifie les paramètres de plateforme à afficher ou à modifier. Vous pouvez spécifier **Any CPU** (valeur par défaut), **x64** ou **x86**.

## <a name="compiler-configuration-options"></a>Options de configuration du compilateur

Les paramètres suivants vous permettent de définir les options de configuration du compilateur.

**Chemin de sortie de la génération**

Spécifie l'emplacement des fichiers de sortie pour cette configuration de projet. Tapez le chemin de la sortie de la génération dans cette zone ou cliquez sur le bouton **Parcourir** pour sélectionner un chemin. Notez que ce chemin est relatif ; si vous entrez un chemin absolu, il sera enregistré comme relatif. Le chemin par défaut est bin\Debug\ ou bin\Release\\.

Grâce aux configurations de build simplifiées, le système de projet détermine s’il faut générer une version Debug ou Release. Si vous cliquez sur la commande **Générer** dans le menu **Déboguer** (F5), la génération est placée dans l’emplacement de débogage, indépendamment du **Chemin de sortie** spécifié. Toutefois, avec la commande **Générer** du menu **Générer**, elle est placée dans l’emplacement spécifié.

**Option Explicit**

Indique s’il faut autoriser la déclaration implicite de variables. Sélectionnez **On** pour exiger la déclaration explicite de variables. Ainsi, le compilateur doit signaler des erreurs si les variables ne sont pas déclarées avant leur utilisation. Sélectionnez **Off** pour autoriser la déclaration implicite de variables.

Ce paramètre correspond à l’option du compilateur [/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit).

Si un fichier de code source contient une [instruction Option Explicit](/dotnet/visual-basic/language-reference/statements/option-explicit-statement), la valeur `On` ou `Off` dans l’instruction remplace le paramètre **Option Explicit** dans la **page Compiler**.

Quand vous créez un projet, le paramètre **Option Explicit** de la **page Compiler** prend la valeur du paramètre **Option Explicit** dans la boîte de dialogue **Options**. Pour afficher ou modifier le paramètre dans cette boîte de dialogue, cliquez sur **Options** dans le menu **Outils**. Dans la boîte de dialogue **Options**, développez **Projets et solutions**, puis cliquez sur **Valeurs par défaut VB**. Le paramètre par défaut initial **Option Explicit** dans **Valeurs par défaut VB** a la valeur **On**.

Il n’est généralement pas recommandé d’affecter à **Option Explicit** la valeur `Off`. Vous risquez de mal orthographier un nom de variable dans un ou plusieurs emplacements, ce qui peut provoquer des résultats inattendus lors de l’exécution du programme.

**Option Strict**

Spécifie s’il faut appliquer la sémantique de type strict. Quand **Option Strict** a la valeur **On**, les conditions suivantes provoquent une erreur de compilation :

- Conversions restrictives implicites

- Liaison tardive

- Saisie implicite qui génère un type `Object`

Les erreurs de conversion restrictive implicite se produisent quand une conversion de types de données implicite est une conversion restrictive. Pour plus d’informations, consultez [Option Strict, instruction](/dotnet/visual-basic/language-reference/statements/option-strict-statement), [Conversions implicites et explicites](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) et [Conversions étendues et restrictives](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions).

Un objet est à liaison tardive quand il est assigné à une propriété ou à une méthode d’une variable déclarée comme étant de type `Object`. Pour plus d’informations, consultez [Option Strict, instruction](/dotnet/visual-basic/language-reference/statements/option-strict-statement) et [Liaison anticipée et liaison tardive](/dotnet/visual-basic/programming-guide/language-features/early-late-binding).

Les erreurs de type d’objet implicite se produisent quand un type approprié ne peut pas être déduit pour une variable déclarée, de sorte qu’un type `Object` est déduit. Cela se produit principalement quand vous utilisez une instruction `Dim` pour déclarer une variable sans utiliser une clause `As` et que `Option Infer` a la valeur Off. Pour plus d’informations, consultez [Option Strict, instruction](/dotnet/visual-basic/language-reference/statements/option-strict-statement), [Option Infer, instruction](/dotnet/visual-basic/language-reference/statements/option-infer-statement) et la [spécification du langage Visual Basic](/dotnet/visual-basic/reference/language-specification).

Le paramètre **Option Strict** correspond à l’option du compilateur [/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict).

Si un fichier de code source contient une [instruction Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement), la valeur `On` ou `Off` dans l’instruction remplace le paramètre **Option Strict** dans la **page Compiler**.

Quand vous créez un projet, le paramètre **Option Strict** de la **page Compiler** prend la valeur du paramètre **Option Strict** dans la boîte de dialogue **Options**. Pour afficher ou modifier le paramètre dans cette boîte de dialogue, cliquez sur **Options** dans le menu **Outils**. Dans la boîte de dialogue **Options**, développez **Projets et solutions**, puis cliquez sur **Valeurs par défaut VB**. Le paramètre par défaut initial **Option Strict** dans **Valeurs par défaut VB** a la valeur **Off**.

**Avertissements individuels - Option Strict**

La section **Configurations des avertissements** de la **page Compiler** contient des paramètres qui correspondent aux trois conditions qui provoquent une erreur de compilation quand `Option Strict` a la valeur On. Voici ces paramètres :

- **Conversion implicite**

- **Liaison tardive ; l’appel peut échouer au moment de l’exécution**

- **Type implicite ; objet pris par défaut**

Quand vous affectez la valeur **On** à **Option Strict**, chacun de ces trois paramètres de configuration d’avertissement prend la valeur **Erreur**. Quand vous affectez la valeur **Off** à **Option Strict**, chacun des trois paramètres prend la valeur **Aucun**.

Vous pouvez remplacer individuellement chaque paramètre de configuration d’avertissement par **Aucun**, **Avertissement** ou **Erreur**. Si les trois paramètres de configuration d’avertissement ont la valeur **Erreur**, `On` s’affiche dans la zone `Option strict`. Si les trois ont la valeur **Aucun**, `Off` apparaît dans cette zone. Pour toute autre combinaison de ces paramètres, **(personnalisé)** s’affiche.

**Option Compare**

Spécifie le type de comparaison de chaînes à utiliser. Sélectionnez **Binary** pour indiquer au compilateur d’utiliser des comparaisons de chaînes binaires respectant la casse. Sélectionnez **Text** pour utiliser des comparaisons de chaînes de texte spécifiques aux paramètres régionaux, qui ne respectent pas la casse.

Ce paramètre correspond à l’option du compilateur [/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare).

Si un fichier de code source contient une [instruction Option Compare](/dotnet/visual-basic/language-reference/statements/option-compare-statement), la valeur `Binary` ou `Text` dans l’instruction remplace le paramètre **Option Compare** dans la **page Compiler**.

Quand vous créez un projet, le paramètre **Option Compare** de la **page Compiler** prend la valeur du paramètre **Option Compare** dans la boîte de dialogue **Options**. Pour afficher ou modifier le paramètre dans cette boîte de dialogue, cliquez sur **Options** dans le menu **Outils**. Dans la boîte de dialogue **Options**, développez **Projets et solutions**, puis cliquez sur **Valeurs par défaut VB**. Le paramètre par défaut initial **Option Compare** dans **Valeurs par défaut VB** a la valeur **Binary**.

**Option Infer**

Indique s’il faut autoriser l’inférence de type de variable locale dans les déclarations de variables. Sélectionnez **On** pour autoriser l’utilisation de l’inférence de type de variable locale. Sélectionnez **Off** pour bloquer l’inférence de type de variable locale.

Ce paramètre correspond à l’option du compilateur [/optioninfer](/dotnet/visual-basic/reference/command-line-compiler/optioninfer).

Si un fichier de code source contient une [instruction Option Infer](/dotnet/visual-basic/language-reference/statements/option-infer-statement), la valeur `On` ou `Off` dans l’instruction remplace le paramètre **Option Infer** dans la **page Compiler**.

Quand vous créez un projet, le paramètre **Option Infer** de la **page Compiler** prend la valeur du paramètre **Option Infer** dans la boîte de dialogue **Options**. Pour afficher ou modifier le paramètre dans cette boîte de dialogue, cliquez sur **Options** dans le menu **Outils**. Dans la boîte de dialogue **Options**, développez **Projets et solutions**, puis cliquez sur **Valeurs par défaut VB**. Le paramètre par défaut initial **Option Infer** dans **Valeurs par défaut VB** a la valeur **On**.

**Unité centrale cible**

Spécifie le processeur devant être ciblé par le fichier de sortie. Spécifiez **x86** pour tout processeur compatible Intel 32 bits, **x64** pour tout processeur compatible Intel 64 bits, **ARM** pour tout processeur ARM ou **Any CPU** pour indiquer que tout processeur est acceptable. **Any CPU** est la valeur par défaut pour les nouveaux projets, car elle permet l’exécution de l’application sur le plus grand nombre de types de matériel.

Pour plus d’informations, consultez [/platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform).

**Préférer 32 bits**

Si la case **Préférer 32 bits** est cochée, l’application s’exécute comme une application 32 bits sur les versions 32 bits et 64 bits de Windows. Sinon, l’application s’exécute comme une application 32 bits sur les versions 32 bits de Windows et comme une application 64 bits sur les versions 64 bits de Windows.

Une exécution en tant qu’application 64 bits double la taille du pointeur et peut provoquer des problèmes de compatibilité avec les bibliothèques qui sont exclusivement 32 bits. Il est judicieux d’exécuter une application comme application 64 bits uniquement si elle s’exécute plus rapidement ou a besoin de plus de 4 Go de mémoire.

Cette case à cocher est disponible uniquement si toutes les conditions suivantes ont remplies :

- Dans la **page Compiler**, la liste **UC cible** a la valeur **Any CPU**.

- Dans la **page Application**, la liste **Type d’application** spécifie que le projet est une application.

- Dans la **page Application**, la liste **Framework cible** spécifie .NET Framework 4.5.

**Configurations des avertissements**

Ce tableau répertorie les conditions de génération et le niveau de notification correspondant : **Aucun**, **Avertissement** ou **Erreur**.

Par défaut, tous les avertissements du compilateur sont ajoutés à la liste des tâches pendant la compilation. Sélectionnez **Désactiver tous les avertissements** pour indiquer au compilateur de ne pas émettre d’avertissements ni d’erreurs. Sélectionnez **Considérer tous les avertissements comme des erreurs** si vous souhaitez que le compilateur traite les avertissements comme des erreurs devant être corrigées.

**Désactiver tous les avertissements**

Spécifie s’il faut autoriser le compilateur à émettre des notifications comme indiqué dans le tableau **Condition et notification** décrit plus haut dans ce document. Par défaut, cette case à cocher est désactivée. Cochez cette case pour indiquer au compilateur de ne pas émettre d’avertissements ni d’erreurs.

Ce paramètre correspond à l’option du compilateur [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn).

**Considérer tous les avertissements comme des erreurs**

Spécifie comment traiter les avertissements. Par défaut, cette case est décochée afin que toutes les notifications d’avertissement conservent la valeur **Avertissement**. Cochez cette case pour remplacer toutes les notifications d’avertissement par **Erreur**.

Cette option est disponible uniquement si **Désactiver tous les avertissements** est décochée.

**Générer le fichier de documentation XML**

Spécifie s’il faut générer des informations de documentation. Par défaut, cette case est cochée pour demander au compilateur de générer des informations de documentation et de les inclure dans un fichier XML. Décochez cette case pour demander au compilateur de ne pas créer de documentation.

Ce paramètre correspond à l’option du compilateur [/doc](/dotnet/visual-basic/reference/command-line-compiler/doc).

**Inscrire pour COM Interop**

Spécifie si votre application managée expose un objet COM (wrapper CCW) qui permet à un objet COM d’interagir avec l’application.

Par défaut, cette case est décochée, ce qui indique que l’application n’autorise pas COM Interop. Cochez cette case pour autoriser COM Interop.

Cette option n’est pas disponible pour les projets d’application Windows ni d’application console.

**Événements de build**

Cliquez sur ce bouton pour accéder à la boîte de dialogue **Événements de build**. Utilisez cette boîte de dialogue pour spécifier les instructions de configuration pré-build et post-build pour le projet. Cette boîte de dialogue s’applique uniquement aux projets Visual Basic. Pour plus d’informations, consultez [Événements de build, boîte de dialogue (Visual Basic)](../../ide/reference/build-events-dialog-box-visual-basic.md).

**Options avancées de compilation**

Cliquez sur ce bouton pour accéder à la boîte de dialogue **Paramètres avancés du compilateur**. Utilisez la boîte de dialogue **Paramètres avancés du compilateur** pour spécifier les propriétés de configuration de build avancées d’un projet. Cette boîte de dialogue s’applique uniquement aux projets Visual Basic. Pour plus d’informations, consultez [Paramètres avancés du compilateur, boîte de dialogue (Visual Basic)](../../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md).

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour spécifier des événements de build (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Compilateur de ligne de commande de Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/index)
- [Guide pratique pour créer et modifier des configurations](../../ide/how-to-create-and-edit-configurations.md)
