---
title: Générer, page du Concepteur de projets (C#)
description: Découvrez comment utiliser la page générer du concepteur de projet dans Visual Studio pour spécifier les propriétés de configuration de build du projet.
ms.custom: SEO-VS-2020
ms.date: 06/20/2017
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuild
helpviewer_keywords:
- Build options [C#]
- Project Designer, Build page
ms.assetid: 77ff1bfc-d633-4634-ba29-9afdb6d7e362
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 91b254f4c075693e23d8f650356cd97e86a4c746
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798555"
---
# <a name="build-page-project-designer-c"></a>Générer, page du Concepteur de projets (C#)

Utilisez la page **Générer** du **Concepteur de projet** pour spécifier les propriétés de configuration de build du projet. Cette page s’applique uniquement aux projets [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)].

Pour accéder à la page **Générer**, choisissez un nœud de projet (pas le nœud **Solution**) dans l’**Explorateur de solutions**. Choisissez ensuite **Affichage**, **Pages de propriétés** dans le menu. Quand le Concepteur de projet s’affiche, cliquez sur l’onglet **Générer**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="configuration-and-platform"></a>Configuration et Plateforme

Les options suivantes vous permettent de sélectionner la configuration et la plateforme à afficher ou à modifier.

> [!NOTE]
> Grâce aux configurations de build simplifiées, le système de projet détermine s’il faut générer une version Debug ou Release. Par conséquent, ces options ne sont pas affichées. Pour plus d’informations, consultez [Guide pratique pour définir des configurations Debug et Release](../../debugger/how-to-set-debug-and-release-configurations.md).

**Configuration**

Spécifie les paramètres de configuration à afficher ou à modifier. Les paramètres peuvent être **Active (Debug)** (valeur par défaut), **Debug**, **Release** ou **Toutes les configurations**.

**Plateforme**

Spécifie les paramètres de plateforme à afficher ou à modifier. Le paramètre par défaut est **Active (Any CPU)**. Vous pouvez modifier la plateforme active à l’aide du **Gestionnaire de configurations**. Pour plus d’informations, consultez [Comment : créer et modifier des configurations](../../ide/how-to-create-and-edit-configurations.md).

## <a name="general"></a>Général

Les options suivantes vous permettent de configurer plusieurs paramètres du compilateur C#.

**Symboles de compilation conditionnelle**

Spécifie les symboles sur lesquels effectuer la compilation conditionnelle. Séparez les symboles par un point-virgule (« ; »). Pour plus d’informations, consultez [/define (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option).

**Définir la constante DEBUG**

Définit DEBUG comme symbole dans tous les fichiers de code source de votre application. Sélectionner cette option équivaut à utiliser l’option de ligne de commande `/define:DEBUG`.

**Définir la constante TRACE**

Définit TRACE comme symbole dans tous les fichiers de code source de votre application. Sélectionner cette option équivaut à utiliser l’option de ligne de commande `/define:TRACE`.

**Plateforme cible**

Spécifie le processeur devant être ciblé par le fichier de sortie. Choisissez **x86** pour tout processeur compatible Intel 32 bits ; choisissez **x64** pour tout processeur compatible Intel 64 bits ; choisissez **ARM** pour les processeurs ARM ; ou choisissez **Any CPU** pour spécifier que tout processeur est acceptable. **Any CPU** est la valeur par défaut pour les projets, car elle permet l’exécution de l’application sur la plus large gamme de matériel.

Pour plus d’informations, consultez [/platform (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option).

**Nullable**

Spécifie le contexte Nullable de l’ensemble du projet. Cette option d’interface utilisateur a été introduite dans Visual Studio 16,5 et n’est activée que pour les projets qui utilisent C# 8,0 ou version ultérieure.

Pour plus d’informations, consultez [contextes Nullable](/dotnet/csharp/nullable-references#nullable-contexts).

**Préférer 32 bits**

Si la case **Préférer 32 bits** est cochée, l’application s’exécute comme une application 32 bits sur les versions 32 bits et 64 bits de Windows. Si elle est décochée, l’application s’exécutera comme une application 32 bits sur les versions 32 bits de Windows et comme une application 64 bits sur les versions 64 bits de Windows.

Si vous exécutez une application comme une application 64 bits, la taille du pointeur double, et des problèmes de compatibilité peuvent se produire avec d’autres bibliothèques qui sont exclusivement de type 32 bits. Il est utile d’exécuter une application 64 bits uniquement si elle a plus besoin de 4 Go de mémoire ou si les instructions 64 bits apportent une amélioration significative des performances.

Cette case à cocher est disponible uniquement si toutes les conditions suivantes ont remplies :

- Dans la **page Générer**, la liste **Plateforme cible** a la valeur **Any CPU**.

- Dans la **page Application**, la liste **Type de sortie** spécifie que le projet est une application.

- Dans la **page Application**, la liste **Framework cible** spécifie .NET Framework 4.5.

**Autoriser les blocs de code unsafe**

Autorise la compilation du code utilisant le mot clé [unsafe](/dotnet/csharp/language-reference/keywords/unsafe). Pour plus d’informations, consultez [/unsafe (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option).

**Optimiser le code**

Active ou désactive les optimisations effectuées par le compilateur pour réduire la taille de votre fichier de sortie, et le rendre plus rapide et plus efficace. Pour plus d’informations, consultez [/optimize (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option).

## <a name="errors-and-warnings"></a>Erreurs et avertissements

Les paramètres suivants sont utilisés pour configurer les options d’erreur et d’avertissement du processus de génération.

**Niveau d’avertissement**

Spécifie le niveau d’affichage pour les avertissements du compilateur. Pour plus d’informations, consultez [/warn (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option).

**Supprimer les avertissements**

Empêche le compilateur de générer un ou plusieurs avertissements. Séparez les numéros des avertissements par une virgule ou un point-virgule. Pour plus d’informations, consultez [/nowarn (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option).

## <a name="treat-warnings-as-errors"></a>Considérer les avertissements comme des erreurs

Les paramètres suivants sont utilisés pour spécifier quels avertissements sont traités comme des erreurs. Sélectionnez l’une des options suivantes pour indiquer dans quelles circonstances retourner une erreur quand la génération rencontre un avertissement. Pour plus d’informations, consultez [/warnaserror (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).

**None** : ne considère aucun avertissement comme des erreurs.

**All** : traite tous les avertissements comme des erreurs.

**Avertissements spécifiques** : traite les avertissements spécifiés comme des erreurs. Séparez les numéros des avertissements par une virgule ou un point-virgule.

> [!TIP]
> Si vous ne souhaitez pas que les avertissements de l’analyse du code soient traités comme des erreurs, consultez [FAQ sur l’analyse du code](/visualstudio/code-quality/analyzers-faq#treat-warnings-as-errors).

## <a name="output"></a>Sortie

Les paramètres suivants sont utilisés pour configurer les options de sortie pour le processus de génération.

**Chemin de sortie**

Spécifie l'emplacement des fichiers de sortie pour cette configuration de projet. Entrez le chemin de la sortie de la génération dans cette zone ou choisissez sur le bouton **Parcourir** pour spécifier un chemin. Ce chemin est relatif ; si vous entrez un chemin absolu, il sera enregistré comme relatif. Le chemin par défaut est bin\Debug ou bin\Release\\.

Grâce aux configurations de build simplifiées, le système de projet détermine s’il faut générer une version Debug ou Release. Si vous cliquez sur la commande **Générer** dans le menu **Déboguer** (F5), la génération est placée dans l’emplacement de débogage, indépendamment du **Chemin de sortie** spécifié. Toutefois, avec la commande **Générer** du menu **Générer**, elle est placée dans l’emplacement spécifié. Pour plus d’informations, consultez [Présentation des configurations de build](../../ide/understanding-build-configurations.md).

**Fichier de documentation XML**

Spécifie le nom d’un fichier dans lequel les commentaires de la documentation seront traités. Pour plus d’informations, consultez [/doc (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option).

**Inscrire pour COM Interop**

Indique que votre application managée exposera un objet COM (un wrapper CCW) qui permet à un objet COM d’interagir avec votre application managée. La propriété **Type de sortie** de la [page Application](../../ide/reference/application-page-project-designer-visual-basic.md) du **Concepteur de projet** pour cette application doit avoir la valeur **Bibliothèque de classes** pour que la propriété **Inscrire pour COM Interop** soit disponible. Pour obtenir un exemple de classe que vous pouvez inclure dans votre application [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] et exposer en tant qu’objet COM, consultez [Exemple de classe COM](/dotnet/csharp/programming-guide/interop/example-com-class).

**Générer un assembly de sérialisation**

Spécifie si le compilateur utilisera l’outil XML Serializer Generator (Sgen.exe) pour créer des assemblys de sérialisation XML. Les assemblys de sérialisation peuvent améliorer les performances de démarrage de <xref:System.Xml.Serialization.XmlSerializer> si vous avez utilisé cette classe pour sérialiser les types dans votre code. Par défaut, cette option a la valeur **Auto**, qui spécifie que les assemblys de sérialisation ne peuvent être générés que si vous avez utilisé <xref:System.Xml.Serialization.XmlSerializer> pour encoder les types dans votre code en XML. **Inactif** spécifie que les assemblys de sérialisation ne doivent jamais être générés, que votre code utilise <xref:System.Xml.Serialization.XmlSerializer> ou non. **Actif** spécifie que les assemblys de sérialisation doivent toujours être générés. Les assemblys de sérialisation sont appelés `TypeName`.XmlSerializers.dll. Pour plus d’informations, consultez [Outil XML Serializer Generator (Sgen.exe)](/dotnet/framework/serialization/xml-serializer-generator-tool-sgen-exe).

**Avancée**

Cliquez pour afficher la [boîte de dialogue Paramètres de génération avancés (C#)](../../ide/reference/advanced-build-settings-dialog-box-csharp.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur les propriétés de projet](../../ide/reference/project-properties-reference.md)
- [Options du compilateur C#](/dotnet/csharp/language-reference/compiler-options/index)
