---
title: Démarrer avec le service linguistique et les extensions d’éditeurs (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 6b151891-c06d-40b1-9867-42298caa8492
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7894efc477e0c406cf8e85f4d3d31df4f2ef97c5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711309"
---
# <a name="get-started-with-language-service-and-editor-extensions"></a>Commencer avec le service linguistique et les extensions d’éditeur
Vous pouvez utiliser des extensions d’éditeurs pour ajouter des fonctionnalités de service linguistique telles que l’en-surface, l’appariement des accolades, IntelliSense et les ampoules à votre propre langage de programmation ou à n’importe quel type de contenu. Vous pouvez également personnaliser l’apparence et le comportement de l’éditeur Visual Studio, par exemple la coloration de texte, les marges, les ornements et d’autres éléments visuels. Vous pouvez également définir votre propre type de contenu et spécifier l’apparence et le comportement des vues de texte dans lesquelles votre contenu apparaît.

 Pour commencer à écrire des extensions d’éditeur, utilisez les modèles de projet d’éditeur qui sont installés dans le cadre du Visual Studio SDK. Le Visual Studio SDK est un ensemble téléchargeable d’outils qui facilitent le développement d’extensions Visual Studio, soit en utilisant VSPackages, soit en utilisant le Cadre d’exténuabilité gérée (MEF).

> [!NOTE]
> Pour plus d’informations sur le Visual Studio SDK, voir [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

 Nous vous recommandons d’en apprendre davantage sur les concepts et les technologies suivants avant d’écrire vos propres extensions d’éditeur.

## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>La Windows Presentation Foundation (WPF) et les extensions d’éditeurs
 L’interface utilisateur de l’éditeur Visual Studio (UI) est implémentée en utilisant la Windows Presentation Foundation (WPF). Le WPF offre une expérience visuelle riche et un modèle de programmation cohérent qui sépare les aspects visuels du code de la logique métier. Vous pouvez utiliser de nombreux éléments et fonctionnalités WPF lorsque vous créez des extensions d’éditeur. Pour plus d’informations, voir [Windows Presentation Foundation](/dotnet/framework/wpf/index).

## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Le Cadre d’exténuabilité gérée (MEF) et les extensions de l’éditeur
 L’éditeur visual Studio utilise le Cadre d’extétiment géré (MEF) pour gérer ses composants et extensions. Le MEF permet également aux développeurs de créer plus facilement des extensions pour une application hôte comme Visual Studio. Dans ce cadre, vous définissez une extension en fonction d’un contrat MEF et l’exportez en tant que partie composante MEF. L’application hôte gère les composants en les trouvant, en les enregistrant et en s’assurant qu’elles sont appliquées au contexte correct.

> [!NOTE]
> Pour plus d’informations sur le MEF dans l’éditeur, voir [Cadre d’exténuabilité gérée dans l’éditeur](../extensibility/managed-extensibility-framework-in-the-editor.md).

## <a name="visual-studio-editor-extension-points-and-extensions"></a>Points d’extension et extensions de l’éditeur Visual Studio
 Les points d’extension de l’éditeur sont des composants MEF que vous pouvez personnaliser et étendre. Dans certains cas, vous étendez le point d’extension en implémentant une interface et en l’exportant avec les métadonnées correctes. Dans d’autres cas, il vous suffit de déclarer une extension et de l’exporter comme un type particulier.

 Voici quelques-uns des types de base d’extensions de l’éditeur :

- Marges et barres de défilement

- Balises

- Ornements

- Options

- IntelliSense

  Pour plus d’informations sur les points d’extension de l’éditeur, voir [Le service de langue et les points d’extension de l’éditeur](../extensibility/language-service-and-editor-extension-points.md).

## <a name="deploying-editor-extensions"></a>Déploiement d’extensions d’éditeurs
 Dans Visual Studio, vous déployez des extensions d’éditeurs en ajoutant un fichier de métadonnées nommé *source.extension.vsixmanifest* à la solution, en construisant la solution, puis en ajoutant une copie des fichiers binaires et le manifeste dans un dossier qui est connu de Visual Studio. Le fichier manifeste définit les faits de base sur l’extension (par exemple, nom, auteur, version et type de contenu). Pour plus d’informations sur le fichier manifeste VSIX et comment déployer des extensions, voir [les extensions Ship Visual Studio](../extensibility/shipping-visual-studio-extensions.md).

 Lorsque vous installez une extension sur un ordinateur, inclure les binaires et le manifeste dans un sous-pliage de dossier qui est connu de Visual Studio.

> [!WARNING]
> Vous n’avez pas à vous soucier des détails des manifestes et des lieux de déploiement si vous utilisez l’un des modèles d’extensibility de l’éditeur qui sont inclus dans Visual Studio. Les modèles contiennent tout ce qui est nécessaire pour enregistrer et déployer une extension.

## <a name="run-extensions-in-the-experimental-instance"></a>Exécuter des extensions dans l’instance expérimentale
 Vous pouvez isoler votre version de travail de Visual Studio pendant que vous développez une extension en la déployant dans le dossier expérimental suivant (sur Windows Vista et Windows 7) :

 *'%LOCALAPPDATA%' 'VisualStudio'10.0Exp’Extensions\\'Société'\\'ExtensionID'*

 lorsque *%LOCALAPPDATA%* est le nom de l’utilisateur connecté, *Société* est le nom de la société qui possède l’extension, et *ExtensionID* est l’ID de l’extension.

 Lorsque vous déployez une extension à l’emplacement expérimental, il s’exécute en mode débogé. Une deuxième instance de Visual Studio est commencée, et est nommé **Microsoft Visual Studio - Experimental Instance**.

## <a name="manage-extensions"></a>Gérer les extensions
 Les extensions au studio visuel sont répertoriées dans **Extensions et Mises à jour** (sur le menu **Tools).** Si vous testez une extension dans le cas expérimental, il est répertorié dans **Extensions et Mises à jour** dans le cas expérimental, mais n’est pas répertorié dans le cas de développement.

 Pour plus d’informations, voir [Localiser et utiliser les extensions Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).

## <a name="use-templates-to-create-editor-extensions"></a>Utilisez des modèles pour créer des extensions d’éditeurs
 Vous pouvez utiliser des modèles d’éditeurs pour créer des extensions MEF qui personnalisent les classificateurs, les ornements et les marges. Il existe des modèles pour les projets C et Visual Basic. Pour plus d’informations, voir [Créer une extension avec un modèle d’élément d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md).

 Vous pouvez également utiliser le modèle de projet VSIX pour créer des extensions. Ce modèle ne fournit que les éléments nécessaires au déploiement de tout type d’extension, et comprend le fichier *source.extension.vsixmanifest,* les références d’assemblage requises, et un fichier de projet qui comprend les tâches de construction qui vous permettent de déployer l’extension. Pour plus d’informations, consultez [le modèle de projet VSIX](../extensibility/vsix-project-template.md).

 Vous pouvez également créer des composants MEF éditeur à partir d’une extension Visual Studio Package. Voir les procédures à pas suivantes pour plus de détails:

- [Procédure pas à pas : Utilisation d’une commande de coquillage avec une extension d’éditeur](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)

- [Procédure pas à pas : Utilisation d’une clé raccourcie avec une extension de l’éditeur](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)

## <a name="see-also"></a>Voir aussi
- [Service linguistique et points d’extension de l’éditeur](../extensibility/language-service-and-editor-extension-points.md)
