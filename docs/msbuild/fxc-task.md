---
title: Tâche FXC | Microsoft Docs
description: En savoir plus sur les paramètres que la tâche FXC MSBuild utilise pour les compilateurs de nuanceur HLSL dans le processus de génération.
ms.custom: SEO-VS-2020
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.fxc
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), FXC task
- FXC task (MSBuild (C++))
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: b200fde9e5bc07f654ae2bf11cd8a752efbfe123
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436696"
---
# <a name="fxc-task"></a>Tâche FXC

Utilisez des compilateurs de nuanceur HLSL dans le processus de génération.

## <a name="parameters"></a>Paramètres

Le tableau suivant décrit les paramètres de la tâche **FXC**.

|Paramètre|Description|
|---------------|-----------------|
|**AdditionalIncludeDirectories**|Paramètre **String []** facultatif.<br/><br/>Spécifie un ou plusieurs répertoires à ajouter au chemin include. Si vous ajoutez plusieurs répertoires, séparez-les par des points-virgules.<br/><br/>Utiliser `/I[path]`.|
|**AdditionalOptions**|Paramètre de **chaîne** facultatif.|
|**AllResourcesBound**|Paramètre **booléen** facultatif.<br/><br/>Le compilateur part du principe que toutes les ressources qu’un nuanceur peut référencer sont liées et en bon état pendant toute la durée de l’exécution du nuanceur. Disponible pour Shader Model 5.1 et les versions ultérieures.<br/><br/>Utiliser `/all_resources_bound`.|
|**AssemblerOutput**|Paramètre de **chaîne** facultatif.<br/><br/>Spécifie le contenu du fichier de sortie linguistique de l’assembly.<br/><br/>Utiliser `/Fc, /Fx`.<br/><br/>**NoListing**<br/>**AssemblyCode**, utilisez `Fc`.<br/>**AssemblyCodeAndHex**, utilisez `Fx`.|
|**AssemblerOutputFile**|Paramètre de **chaîne** facultatif.<br/><br/>Spécifie le nom de fichier du fichier listing du code d’assembly.|
|**CompileD2DCustomEffect**|Paramètre **booléen** facultatif.<br/><br/>Compilez un effet personnalisé Direct2D qui contient des nuanceurs de pixels. N’utilisez pour un vertex ni ne calculez un effet personnalisé.|
|**ConsumeExportFile**|Paramètre de **chaîne** facultatif.|
|**DisableOptimizations**|Paramètre **booléen** facultatif.<br/><br/>Désactivez les optimisations.<br/><br/>`/Od` implique `/Gfp` bien que la sortie ne puisse pas être identique à `/Od /Gfp`.|
|**EnableDebuggingInformation**|Paramètre **booléen** facultatif.<br/><br/>Activez les informations de débogage.|
|**EnableUnboundedDescriptorTables**|Paramètre **booléen** facultatif.<br/><br/>Indiquez au compilateur qu’un nuanceur peut contenir une déclaration d’un tableau de ressources avec une plage illimitée. Disponible pour Shader Model 5.1 et les versions ultérieures.<br/><br/>Utiliser `/enable_unbounded_descriptor_tables`.|
|**EntryPointName**|Paramètre de **chaîne** facultatif.<br/><br/>Spécifie le nom du point d’entrée pour le nuanceur.<br/><br/>Utiliser `/E[name]`.|
|**GenerateExportFile**|Paramètre de **chaîne** facultatif.|
|**GenerateExportShaderProfile**|Paramètre de **chaîne** facultatif.|
|**HeaderFileOutput**|Paramètre de **chaîne** facultatif.<br/><br/>Spécifie un nom pour le fichier d’en-tête contenant le code objet.<br/><br/>Utiliser `/Fh [name]`.|
|**ObjectFileOutput**|Paramètre de **chaîne** facultatif.<br/><br/>Spécifie un nom pour le fichier objet.<br/><br/>Utiliser `/Fo [name]`.|
|**PreprocessorDefinitions**|Paramètre **String []** facultatif.<br/><br/>Définit les symboles de prétraitement pour votre fichier source.|
|**SetRootSignature**|Paramètre de **chaîne** facultatif.<br/><br/>Attachez la signature racine au bytecode du nuanceur. Disponible pour Shader Model 5.0 et les versions ultérieures.<br/><br/>Utiliser `/setrootsignature`.|
|**ShaderModel**|Paramètre de **chaîne** facultatif.<br/><br/>Spécifie le modèle de nuanceur. Certains types de nuanceur peuvent uniquement être utilisés avec les modèles récents de nuanceur.<br/><br/>Utiliser `/T [type]_[model]`.|
|**ShaderType**|Paramètre de **chaîne** facultatif.<br/><br/>Spécifie le type de nuanceur.<br/><br/>Utiliser `/T [type]_[model]`.<br/><br/>**Effect**, utilisez `fx`.<br/>**Vertex**, utilisez `vs`.<br/>**Pixel**, utilisez `ps`.<br/>**Geometry**, utilisez `gs`.<br/>**Hull**, utilisez `hs`.<br/>**Domain**, utilisez `ds`.<br/>**Compute**, utilisez `cs`.<br/>**Library**, utilisez `lib`.<br/>**RootSignature**, générez un objet de signature racine.|
|**Source**|Paramètre **ITaskItem** obligatoire.|
|**SuppressStartupBanner**|Paramètre **booléen** facultatif.<br/><br/>Supprime l’affichage de la bannière de démarrage et des messages d’information.<br/><br/>Utiliser `/nologo`.|
|**TrackerLogDirectory**|Paramètre de **chaîne** facultatif.|
|**TreatWarningAsError**|Paramètre **booléen** facultatif.<br/><br/>Considère tous les avertissements du compilateur comme des erreurs.<br/><br/>Pour un nouveau projet, il est conseillé d’utiliser `/WX` dans toutes les compilations, car la résolution de tous les avertissements permet de réduire les erreurs de code difficilement détectables.|
|**VariableName**|Paramètre de **chaîne** facultatif.<br/><br/>Spécifie un nom pour la variable dans le fichier d’en-tête.<br/><br/>Utiliser `/Vn [name]`.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)