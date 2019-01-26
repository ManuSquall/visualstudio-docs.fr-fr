---
title: Prise en charge de NGen dans VSIX v3 | Microsoft Docs
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b316efe4abc9f14608db2e61602ac882c7208234
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54958691"
---
# <a name="ngen-support-in-vsix-v3"></a>Prise en charge de Ngen dans VSIX v3

Avec Visual Studio 2017 et le nouveau v3 VSIX (version 3) manifeste d’extension format, extension les développeurs peuvent désormais « ngen » leurs assemblys au moment de l’installation.

Voici un extrait à partir de MSDN qui explique quelles « ngen » fait :

>Le Générateur d’images natives (*Ngen.exe*) est un outil qui améliore les performances des applications managées. *Ngen.exe* crée des images natives, qui sont des fichiers contenant le code machine compilé spécifique au processeur et les installe dans le cache des images natives sur l’ordinateur local. Le runtime peut utiliser des images natives du cache plutôt que le compilateur juste-à-temps (JIT) pour compiler l'assembly d'origine.
>
>à partir de [Ngen.exe (Native Image Generator)](/dotnet/framework/tools/ngen-exe-native-image-generator)

Dans l’ordre de « ngen » un assembly, l’extension VSIX doit être installé « par instance par ordinateur ». Cela peut être activée en cochant la case à cocher « tous les utilisateurs » le `extension.vsixmanifest` concepteur :

![Vérifiez tous les utilisateurs](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>L’activation de Ngen

Pour activer ngen pour un assembly, vous pouvez utiliser la **propriétés** fenêtre dans Visual Studio.

Il existe 4 propriétés qui peuvent être définies :

1. **Ngen** (booléen) - si la valeur est true, le programme d’installation de Visual Studio sera « ngen » de l’assembly.
2. **Application Ngen** (chaîne) - Ngen offre la possibilité d’utiliser d’une application *app.config* fichier afin de résoudre les dépendances d’assembly. Cette valeur doit être définie à une application dont la propriété *app.config* vous souhaitez utiliser (par rapport au répertoire d’installation de Visual Studio).
3. **Ngen Architecture** (énumération) - l’architecture de compiler en mode natif votre assembly. Les options sont : un. NotSpecified b. X86 c. X64 d. Tous
4. **Priorité de Ngen** (entier compris entre 1 et 3) - niveau de la priorité de Ngen est décrit à l’adresse [les niveaux de priorité de Ngen.exe](/dotnet/framework/tools/ngen-exe-native-image-generator#priority-levels).

Voici un aperçu de la **propriétés** fenêtre en action :

![Ngen dans les propriétés](media/ngen-in-properties.png)

Cette opération ajoute des métadonnées à la référence de projet à l’intérieur du projet VSIX *.csproj* fichier :

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
    <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
    <Name>ClassLibrary1</Name>
    <Ngen>True</Ngen>
    <NgenApplication>vsn.exe</NgenApplication>
    <NgenArchitecture>X86</NgenArchitecture>
    <NgenPriority>2</NgenPriority>
</ProjectReference>
 ```

 >**Remarque :** Vous pouvez modifier le fichier .csproj directement, si vous préférez.

## <a name="extra-information"></a>Informations supplémentaires

Les modifications de Concepteur de propriété s’appliquent aux plus que les références de projet ; Vous pouvez définir les métadonnées de Ngen pour les éléments à l’intérieur de votre projet (en utilisant les mêmes méthodes décrites ci-dessus) tant que les éléments sont des assemblys .NET.