---
title: Paramètres de génération avancés, boîte de dialogue (C#)
ms.date: 08/05/2019
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- cs.AdvancedBuildSettings
helpviewer_keywords:
- Build options [C#], advanced
ms.assetid: 141f2dee-1563-4ce6-ba37-32920b082519
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 917ef4ff685c243fa271a0966a931151cb12ed2b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85418845"
---
# <a name="advanced-build-settings-dialog-box-c"></a>Paramètres de génération avancés, boîte de dialogue (C#)

Utilisez la boîte de dialogue **Paramètres de génération avancés** du **Concepteur de projet** pour spécifier les propriétés avancées de configuration de build du projet. Cette boîte de dialogue s’applique uniquement aux projets C#.

## <a name="general"></a>Général

Les options suivantes permettent de définir des paramètres généraux avancés.

**Version du langage**

::: moniker range=">=vs-2019"

Renvoie à [/langversion (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option), qui fournit des informations sur la façon dont une version de langage par défaut est choisie en fonction du Framework cible d’un projet.

::: moniker-end

::: moniker range="vs-2017"

Spécifie la version du langage à utiliser. L’ensemble de fonctionnalités est différent pour chacune des versions. Cette option peut donc être utilisée pour forcer le compilateur à autoriser uniquement un sous-ensemble des fonctionnalités implémentées, ou à activer uniquement les fonctionnalités conformes à une norme existante.

La valeur par défaut est C# 7,0.

::: moniker-end

**Rapport d’erreurs du compilateur interne**

Spécifie s’il faut signaler les erreurs du compilateur à Microsoft. Si la valeur est **prompt** (valeur par défaut), une invite s’affiche en cas d’erreur interne du compilateur, et vous donne la possibilité d’envoyer un rapport d’erreurs par voie électronique à Microsoft. Si la valeur est **send**, un rapport d’erreurs est envoyé automatiquement. Si la valeur est **queue**, les rapports d’erreurs sont mis en file attente. Si la valeur est **none**, l’erreur est signalée uniquement dans la sortie de texte du compilateur. Pour plus d’informations, consultez [/errorreport (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option).

**Vérifier les dépassements de capacité arithmétiques positifs et négatifs**

Spécifie si une instruction arithmétique entière hors de portée des mots clés [checked](/dotnet/csharp/language-reference/keywords/checked) ou [unchecked](/dotnet/csharp/language-reference/keywords/unchecked), dont la valeur n’est pas comprise dans la plage du type de données, doit provoquer la levée d’une exception à l’exécution. Pour plus d’informations, consultez l' [option/Checked (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option).

**Ne pas référencer mscorlib.dll**

Spécifie si mscorlib.dll doit être importé dans votre programme, en définissant l’intégralité de l’espace de noms <xref:System>. Cochez cette case pour définir ou créer vos propres objets et espaces de noms <xref:System>. Pour plus d’informations, consultez [/nostdlib (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option).

## <a name="output"></a>Output

Les options suivantes permettent de spécifier des options de sortie avancées.

**Informations de débogage**

Indique le type d'informations de débogage générées par le compilateur. Pour plus d’informations sur la configuration des performances de débogage d’une application, consultez [Simplification du débogage d’une image](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug). Ce paramètre a les options suivantes :

- **Aucune**

   Spécifie que les informations de débogage ne doivent pas être générées.

- **full**

   Permet d’attacher un débogueur au programme en cours d’exécution.

- **pdbonly**

   Active le débogage du code source lorsque le programme est démarré dans le débogueur, mais affiche uniquement un assembleur quand le programme en cours d’exécution est attaché au débogueur.

- **portable**

   Génère un fichier .PDB, un fichier de symboles portable non spécifique à la plateforme qui fournit d’autres outils, notamment des débogueurs, des informations sur les éléments dans le fichier exécutable principal et la façon dont il a été produit. Pour plus d’informations, consultez [PDB portable](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md).

- **Embedded**

   Incorpore les informations de symboles portables dans l’assembly. Aucun fichier .PDB externe n’est produit.

Pour plus d’informations, consultez [/debug (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).

**Alignement des fichiers**

Spécifie la taille des sections dans le fichier de sortie. Les valeurs valides sont **512**, **1024**, **2048**, **4096**et **8192**. Ces valeurs sont mesurées en octets. Chaque section est alignée sur une limite qui est un multiple de cette valeur, affectant ainsi la taille du fichier de sortie. Pour plus d’informations, consultez [/filealign (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option).

**Adresse de base de la bibliothèque**

Spécifie l'adresse de base préférée à laquelle charger une DLL. L’adresse de base par défaut d’une DLL est définie par le Common Language Runtime (CLR) .NET Framework. Pour plus d’informations, consultez [/BaseAddress (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option).

## <a name="see-also"></a>Voir aussi

- [Options du compilateur C#](/dotnet/csharp/language-reference/compiler-options/index)
- [Générer, page du concepteur de projets (C#)](../../ide/reference/build-page-project-designer-csharp.md)
