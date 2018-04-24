---
title: Types de fichiers projet et solution | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- File Properties.CopyToOutputDirectory
- File Properties.CustomToolNamespace
- File Properties.FileName
- File Properties.FullPath
- File Properties.BuildAction
- File Properties.CustomTool
- FileProperties
helpviewer_keywords:
- .sln files
- .suo files
- file types [Visual Studio]
- file extensions [Visual Studio]
- solution files [Visual Studio]
- sln files
- suo files
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3cc172d53e326d5bb20668f6919e887eca39f582
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="project-and-solution-file-types"></a>Types de fichiers projet et solution

Visual Studio prend en charge de nombreux types de fichiers. Dans une installation particulière, les composants installés déterminent les types de fichiers pris en charge. Cette rubrique répertorie les types de fichiers solution et projet qui sont pris en charge dans certaines installations standard.

## <a name="solution-files-sln-and-suo"></a>Fichiers solution (.sln et .suo)

Visual Studio utilise deux types de fichiers (.sln et .suo) pour stocker les paramètres des solutions. Ces fichiers, appelés collectivement fichiers solution, fournissent à l'Explorateur de solutions les informations dont il a besoin pour afficher une interface graphique de gestion de vos fichiers.

|Extension|Name|Description|
|---------------|----------|-----------------|
|.sln|Solution Visual Studio|Organise les projets, les éléments de projet et les éléments de solution dans la solution.|
|.suo|Options utilisateur de solution|Assure le suivi des personnalisations au niveau de l’utilisateur que vous avez effectuées dans Visual Studio, telles que les points d’arrêt.|

## <a name="project-files"></a>Fichiers projet

Les projets peuvent contenir de nombreux types de fichiers. Par exemple, les fichiers de code C# ont une extension **.cs** et les fichiers C++ ont une extension **.cpp**. Les ressources sont stockées dans des fichiers **.resx** et le code XAML dans des fichiers **.xaml**. Les fichiers [App.config](../../ide/managing-application-settings-dotnet.md) contiennent des informations sur l’application qui ne doivent pas être incluses dans le code d’application (par exemple les chaînes de connexion).

Pour plus d’informations sur les types de fichiers dans les projets C++, consultez [Types de fichiers créés pour les projets Visual C++](/cpp/ide/file-types-created-for-visual-cpp-projects).

## <a name="see-also"></a>Voir aussi

[Projets et solutions](../../ide/solutions-and-projects-in-visual-studio.md)