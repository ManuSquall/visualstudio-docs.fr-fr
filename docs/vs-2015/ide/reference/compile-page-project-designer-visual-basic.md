---
title: Page Compiler, Concepteur de projets (Visual Basic) │ Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 65
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: db830e04388b7465c941e2fdf069b49f98951a1f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660827"
---
# <a name="compile-page-project-designer-visual-basic"></a>Page Compiler, Concepteur de projets (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La page **Compiler** du Concepteur de projets vous permet de spécifier les instructions de compilation. Vous pouvez également spécifier dans cette page les options avancées du compilateur et les événements pré-build ou post-build.

 Pour accéder à la page **Compiler**, choisissez un nœud de projet (pas le nœud **Solution**) dans **l’Explorateur de solutions**. Ensuite, choisissez **Projet**, **Propriétés** dans la barre de menus. Quand le Concepteur de projets apparaît, cliquez sur l’onglet **Compiler**.

 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

## <a name="configuration-and-platform"></a>Configuration et Plateforme
 Les paramètres suivants vous permettent de sélectionner la configuration et la plateforme à afficher ou à modifier.

> [!NOTE]
> Grâce aux configurations de build simplifiées, le système de projet détermine s’il faut générer une version Debug ou Release. Par conséquent, les listes **Configuration** et **Plateforme** ne sont pas affichées. Pour plus d’informations, consultez [Configurations de projet Debug et Release](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

 **Configuration** Spécifie les paramètres de configuration à afficher ou à modifier. Les paramètres sont **Debug** (valeur par défaut), **Release** ou **Toutes les configurations**. Pour plus d’informations, consultez [Configurations de projet Debug et Release](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e) et [Guide pratique pour créer et modifier des configurations](../../ide/how-to-create-and-edit-configurations.md).

 **Plateforme** Spécifie les paramètres de plateforme à afficher ou à modifier. Vous pouvez spécifier **Any CPU** (valeur par défaut), **x64** ou **x86**. Pour plus d’informations, consultez [Configurations de projet Debug et Release](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

## <a name="compiler-configuration-options"></a>Options de configuration du compilateur
 Les paramètres suivants vous permettent de définir les options de configuration du compilateur.

 **Chemin de sortie** de la génération Spécifie l’emplacement des fichiers de sortie pour la configuration de ce projet. Tapez le chemin de la sortie de la génération dans cette zone ou cliquez sur le bouton **Parcourir** pour sélectionner un chemin. Notez que ce chemin est relatif ; si vous entrez un chemin absolu, il sera enregistré comme relatif. Le chemin par défaut est bin\Debug\ ou bin\Release\\. Pour plus d’informations, consultez [Configurations de projet Debug et Release](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

 Grâce aux configurations de build simplifiées, le système de projet détermine s’il faut générer une version Debug ou Release. Si vous cliquez sur la commande **Générer** dans le menu **Déboguer** (F5), la génération est placée dans l’emplacement de débogage, indépendamment du **Chemin de sortie** spécifié. Toutefois, avec la commande **Générer** du menu **Générer**, elle est placée dans l’emplacement spécifié. Pour plus d’informations, consultez [Configurations de projet Debug et Release](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

 **Option explicit** Spécifie si la déclaration implicite des variables est autorisée. Sélectionnez **On** pour exiger la déclaration explicite de variables. Ainsi, le compilateur doit signaler des erreurs si les variables ne sont pas déclarées avant leur utilisation. Sélectionnez **Off** pour autoriser la déclaration implicite de variables.

 Ce paramètre correspond à l’option du compilateur [/optionexplicit](https://msdn.microsoft.com/library/5d296ab3-bafe-4c4d-9887-78f162ed86c7).

 Si un fichier de code source contient une [instruction Option Explicit](https://msdn.microsoft.com/library/e82ac1ad-2cd3-49b2-b985-8bcf016f3fcc), la valeur `On` ou `Off` dans l’instruction remplace le paramètre **Option Explicit** dans la **page Compiler**.

 Quand vous créez un projet, le paramètre **Option Explicit** de la **page Compiler** prend la valeur du paramètre **Option Explicit** dans la boîte de dialogue **Options**. Pour afficher ou modifier le paramètre dans cette boîte de dialogue, cliquez sur **Options** dans le menu **Outils**. Dans la boîte de dialogue **Options**, développez **Projets et solutions**, puis cliquez sur **Valeurs par défaut VB**. Le paramètre par défaut initial **Option Explicit** dans **Valeurs par défaut VB** a la valeur **On**.

 Il n’est généralement pas recommandé d’affecter à **Option Explicit** la valeur `Off`. Vous risquez de mal orthographier un nom de variable dans un ou plusieurs emplacements, ce qui peut provoquer des résultats inattendus lors de l’exécution du programme.

 **Option strict** Spécifie si la sémantique de type stricte est appliquée. Quand **Option Strict** a la valeur **On**, les conditions suivantes provoquent une erreur de compilation :

- Conversions restrictives implicites

- Liaison tardive

- Saisie implicite qui génère un type `Object`

  Les erreurs de conversion restrictive implicite se produisent quand une conversion de types de données implicite est une conversion restrictive. Pour plus d’informations, consultez [Option Strict, instruction](https://msdn.microsoft.com/library/5883e0c1-a920-4274-8e46-b0ff047eaee5), [Conversions implicites et explicites](https://msdn.microsoft.com/library/77de1659-af8a-492c-967e-e7ef60ccce66) et [Conversions étendues et restrictives](https://msdn.microsoft.com/library/058c3152-6c28-4268-af44-2209e774f0bd).

  Un objet est à liaison tardive quand il est assigné à une propriété ou à une méthode d’une variable déclarée comme étant de type `Object`. Pour plus d’informations, consultez [Option Strict, instruction](https://msdn.microsoft.com/library/5883e0c1-a920-4274-8e46-b0ff047eaee5) et [Liaison anticipée et liaison tardive](https://msdn.microsoft.com/library/d6ff7f1e-b94f-4205-ab8d-5cfa91758724).

  Les erreurs de type d’objet implicite se produisent quand un type approprié ne peut pas être déduit pour une variable déclarée, de sorte qu’un type `Object` est déduit. Cela se produit principalement quand vous utilisez une instruction `Dim` pour déclarer une variable sans utiliser une clause `As` et que `Option Infer` a la valeur Off. Pour plus d’informations, consultez [Option Strict, instruction](https://msdn.microsoft.com/library/5883e0c1-a920-4274-8e46-b0ff047eaee5), [Option Infer, instruction](https://msdn.microsoft.com/library/4ad3e6e9-8f5b-4209-a248-de22ef6e4652) et la [spécification du langage Visual Basic](https://msdn.microsoft.com/library/42c30017-19d0-442e-87a2-850b66ddc3df).

  Le paramètre **Option Strict** correspond à l’option du compilateur [/optionstrict](https://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da).

  Si un fichier de code source contient une [instruction Option Strict](https://msdn.microsoft.com/library/5883e0c1-a920-4274-8e46-b0ff047eaee5), la valeur `On` ou `Off` dans l’instruction remplace le paramètre **Option Strict** dans la **page Compiler**.

  Quand vous créez un projet, le paramètre **Option Strict** de la **page Compiler** prend la valeur du paramètre **Option Strict** dans la boîte de dialogue **Options**. Pour afficher ou modifier le paramètre dans cette boîte de dialogue, cliquez sur **Options** dans le menu **Outils**. Dans la boîte de dialogue **Options**, développez **Projets et solutions**, puis cliquez sur **Valeurs par défaut VB**. Le paramètre par défaut initial **Option Strict** dans **Valeurs par défaut VB** a la valeur **Off**.

  **Avertissements individuels option strict.** La section **Configurations des avertissements** de la **page Compiler** contient des paramètres qui correspondent aux trois conditions qui provoquent une erreur de compilation quand `Option Strict` a la valeur On. Voici ces paramètres :

- **Conversion implicite**

- **Liaison tardive ; l’appel peut échouer au moment de l’exécution**

- **Type implicite ; objet pris par défaut**

  Quand vous affectez la valeur **On** à **Option Strict**, chacun de ces trois paramètres de configuration d’avertissement prend la valeur **Erreur**. Quand vous affectez la valeur **Off** à **Option Strict**, chacun des trois paramètres prend la valeur **Aucun**.

  Vous pouvez remplacer individuellement chaque paramètre de configuration d’avertissement par **Aucun**, **Avertissement** ou **Erreur**. Si les trois paramètres de configuration d’avertissement sont définis sur **erreur**, `On` apparaît dans la `Option strict` zone. Si les trois sont définis sur **aucun**, `Off` s’affiche dans cette zone. Pour toute autre combinaison de ces paramètres, **(personnalisé)** s’affiche.

  **Option compare** Spécifie le type de comparaison de chaîne à utiliser. Sélectionnez **Binary** pour indiquer au compilateur d’utiliser des comparaisons de chaînes binaires respectant la casse. Sélectionnez **Text** pour utiliser des comparaisons de chaînes de texte spécifiques aux paramètres régionaux, qui ne respectent pas la casse.

  Ce paramètre correspond à l’option du compilateur [/optioncompare](https://msdn.microsoft.com/library/7237b766-b44d-4cc5-9a3c-885348a7d9e4).

  Si un fichier de code source contient une [instruction Option Compare](https://msdn.microsoft.com/library/54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e), la valeur `Binary` ou `Text` dans l’instruction remplace le paramètre **Option Compare** dans la **page Compiler**.

  Quand vous créez un projet, le paramètre **Option Compare** de la **page Compiler** prend la valeur du paramètre **Option Compare** dans la boîte de dialogue **Options**. Pour afficher ou modifier le paramètre dans cette boîte de dialogue, cliquez sur **Options** dans le menu **Outils**. Dans la boîte de dialogue **Options**, développez **Projets et solutions**, puis cliquez sur **Valeurs par défaut VB**. Le paramètre par défaut initial **Option Compare** dans **Valeurs par défaut VB** a la valeur **Binary**.

  **Option infer** Spécifie si l’inférence de type de variable locale est autorisée dans les déclarations de variable. Sélectionnez **On** pour autoriser l’utilisation de l’inférence de type de variable locale. Sélectionnez **Off** pour bloquer l’inférence de type de variable locale.

  Ce paramètre correspond à l’option du compilateur [/optioninfer](https://msdn.microsoft.com/library/f6c09db1-0553-464a-abe3-d4510c61d6ed).

  Si un fichier de code source contient une [instruction Option Infer](https://msdn.microsoft.com/library/4ad3e6e9-8f5b-4209-a248-de22ef6e4652), la valeur `On` ou `Off` dans l’instruction remplace le paramètre **Option Infer** dans la **page Compiler**.

  Quand vous créez un projet, le paramètre **Option Infer** de la **page Compiler** prend la valeur du paramètre **Option Infer** dans la boîte de dialogue **Options**. Pour afficher ou modifier le paramètre dans cette boîte de dialogue, cliquez sur **Options** dans le menu **Outils**. Dans la boîte de dialogue **Options**, développez **Projets et solutions**, puis cliquez sur **Valeurs par défaut VB**. Le paramètre par défaut initial **Option Infer** dans **Valeurs par défaut VB** a la valeur **On**.

  **Cible CPU** Spécifie le processeur à cibler par le fichier de sortie. Spécifiez **x86** pour tout processeur compatible Intel 32 bits, **x64** pour tout processeur compatible Intel 64 bits, **ARM** pour tout processeur ARM ou **Any CPU** pour indiquer que tout processeur est acceptable. **Any CPU** est la valeur par défaut pour les nouveaux projets, car elle permet l’exécution de l’application sur le plus grand nombre de types de matériel.

  Pour plus d’informations, consultez [/platform (Visual Basic)](https://msdn.microsoft.com/library/f9bc61e6-e854-4ae1-87b9-d6244de23fd1).

  **Préférer 32 bits** Si la case **Préférer 32 bits** est cochée, l’application s’exécute comme une application 32 bits sur les versions 32 bits et 64 bits de Windows. Sinon, l’application s’exécute comme une application 32 bits sur les versions 32 bits de Windows et comme une application 64 bits sur les versions 64 bits de Windows.

  Une exécution en tant qu’application 64 bits double la taille du pointeur et peut provoquer des problèmes de compatibilité avec les bibliothèques qui sont exclusivement 32 bits. Il est judicieux d’exécuter une application comme application 64 bits uniquement si elle s’exécute plus rapidement ou a besoin de plus de 4 Go de mémoire.

  Cette case à cocher est disponible uniquement si toutes les conditions suivantes ont remplies :

- Dans la **page Compiler**, la liste **UC cible** a la valeur **Any CPU**.

- Dans la **page Application**, la liste **Type d’application** spécifie que le projet est une application.

- Dans la **page Application**, la liste **Framework cible** spécifie .NET Framework 4.5.

  **Configurations des avertissements** Ce tableau liste les conditions de génération et le niveau de notification correspondant : **Aucun**, **Avertissement** ou **Erreur**.

  Par défaut, tous les avertissements du compilateur sont ajoutés à la liste des tâches pendant la compilation. Sélectionnez **Désactiver tous les avertissements** pour indiquer au compilateur de ne pas émettre d’avertissements ni d’erreurs. Sélectionnez **Considérer tous les avertissements comme des erreurs** si vous souhaitez que le compilateur traite les avertissements comme des erreurs devant être corrigées.

  **Désactiver tous les avertissements** Spécifie si le compilateur est autorisé à émettre les notifications indiquées dans le tableau **Condition et notification** décrit plus haut dans ce document. Par défaut, cette case à cocher est désactivée. Cochez cette case pour indiquer au compilateur de ne pas émettre d’avertissements ni d’erreurs.

  Ce paramètre correspond à l’option du compilateur [/nowarn](https://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83).

  **Considérer tous les avertissements comme des erreurs** Spécifie comment traiter les avertissements. Par défaut, cette case est décochée afin que toutes les notifications d’avertissement conservent la valeur **Avertissement**. Cochez cette case pour remplacer toutes les notifications d’avertissement par **Erreur**.

  Cette option est disponible uniquement si **Désactiver tous les avertissements** est décochée.

  **Générer le fichier de documentation XML** Spécifie si des informations de documentation doivent être générées. Par défaut, cette case est cochée pour demander au compilateur de générer des informations de documentation et de les inclure dans un fichier XML. Décochez cette case pour demander au compilateur de ne pas créer de documentation.

  Ce paramètre correspond à l’option du compilateur [/doc](https://msdn.microsoft.com/library/5fc32ec9-a149-4648-994c-a8d0cccd0a65).

  **Inscrire pour COM Interop** Spécifie si votre application managée expose un objet COM (wrapper CCW (COM Callable Wrapper)) qui permet à un objet COM d’interagir avec l’application.

  Par défaut, cette case est décochée, ce qui indique que l’application n’autorise pas COM Interop. Cochez cette case pour autoriser COM Interop.

  Cette option n’est pas disponible pour les projets d’application Windows ni d’application console.

  **Événements de build** Cliquez sur ce bouton pour accéder à la boîte de dialogue **Événements de build**. Utilisez cette boîte de dialogue pour spécifier les instructions de configuration pré-build et post-build pour le projet. Cette boîte de dialogue s’applique uniquement aux projets Visual Basic. Pour plus d’informations, consultez [Événements de build, boîte de dialogue (Visual Basic)](../../ide/reference/build-events-dialog-box-visual-basic.md).

  **Options avancées de compilation** Cliquez sur ce bouton pour accéder à la boîte de dialogue **Paramètres avancés du compilateur**. Utilisez la boîte de dialogue **Paramètres avancés du compilateur** pour spécifier les propriétés de configuration de build avancées d’un projet. Cette boîte de dialogue s’applique uniquement aux projets Visual Basic. Pour plus d’informations, consultez [Paramètres avancés du compilateur, boîte de dialogue (Visual Basic)](../../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md).

## <a name="see-also"></a>Voir aussi
 [Configurations de projet Debug et Release](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e) [gestion des propriétés de compilation](https://msdn.microsoft.com/94308881-f10f-4caf-a729-f1028e596a2c) [Comment : spécifier des événements de build (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md) [Visual Basic compilateur de ligne de commande](https://msdn.microsoft.com/library/6b57c444-50c7-4b88-8f59-ed65cff5e05c) [Comment : créer et modifier des configurations](../../ide/how-to-create-and-edit-configurations.md)
