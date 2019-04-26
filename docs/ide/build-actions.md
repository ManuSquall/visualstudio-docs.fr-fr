---
title: Actions de génération pour les fichiers
ms.date: 11/19/2018
ms.technology: vs-ide-compile
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7820cbbe0477000c2a822e94f5204906d65025fa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62975642"
---
# <a name="build-actions"></a>Actions de génération

Tous les fichiers d’un projet Visual Studio ont une action de génération. L’action de génération contrôle ce qui arrive au fichier quand le projet est compilé.

> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [Actions de génération dans Visual Studio pour Mac](/visualstudio/mac/build-actions).

## <a name="set-a-build-action"></a>Définir une action de génération

Pour définir l’action de génération concernant un fichier, ouvrez les propriétés du fichier dans la fenêtre **Propriétés** en le sélectionnant dans l’**Explorateur de solutions** et en appuyant sur **Alt**+**Entrée**. Vous pouvez aussi cliquer avec le bouton droit sur le fichier dans l’**Explorateur de solutions**, puis choisir **Propriétés**. Dans la fenêtre **Propriétés**, dans la section **Avancé**, utilisez la liste déroulante en regard d’**Action de génération** afin de définir une action de génération pour le fichier.

![Actions de génération pour un fichier dans Visual Studio](media/build-actions.png)

## <a name="build-action-values"></a>Valeurs des actions de génération

Voici certaines actions de génération pour les fichiers projet C# et Visual Basic :

* **Aucune** : le fichier ne fait pas du tout partie de la build. Cette valeur peut être utilisée pour les fichiers de documentation tels que les fichiers « Lisez-moi ».
* **Compiler** : le fichier est passé comme fichier source au compilateur.
* **Contenu** : un fichier marqué comme **Contenu** peut être récupéré sous la forme d’un flux par le biais d’un appel à <xref:System.Windows.Application.GetContentStream%2A?displayProperty=nameWithType>. Pour les projets ASP.NET, ces fichiers sont ajoutés pour faire partie du site au moment de son déploiement.
* **Ressource incorporée** : le fichier est passé au compilateur comme ressource à incorporer dans l’assembly. Vous pouvez appeler <xref:System.Reflection.Assembly.GetManifestResourceStream%2A?displayProperty=fullName> pour lire le fichier à partir de l’assembly.
* **Fichiers supplémentaires** : fichier texte non-source passé au compilateur C# ou Visual Basic en tant qu’entrée. Cette action de génération est principalement utilisée pour fournir des entrées aux [analyseurs](../code-quality/roslyn-analyzers-overview.md) qui sont référencés par un projet pour vérifier la qualité du code. Pour plus d’informations, consultez [Utiliser des fichiers supplémentaires](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Using%20Additional%20Files.md).

## <a name="see-also"></a>Voir aussi

- [Options du compilateur C#](/dotnet/csharp/language-reference/compiler-options/listed-alphabetically)
- [Options du compilateur Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically)
- [Actions de génération (Visual Studio pour Mac)](/visualstudio/mac/build-actions)