---
title: Prise en charge Ngen VSIX v3 | Documents Microsoft
ms.custom: ''
ms.date: 11/09/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 146df23bff14bd93558c645521f99f6099a49bde
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31139758"
---
# <a name="ngen-support-in-vsix-v3"></a>Prise en charge Ngen VSIX v3

Avec Visual Studio 2017 et la v3 VSIX nouvelle extension (version 3) manifeste format, extension les développeurs peuvent désormais « ngen » leurs assemblys au moment de l’installation.

Voici un extrait à partir de MSDN qui explique quelles « ngen » fait :

>L'outil Native Image Generator Tool (Ngen.exe) est un outil qui améliore les performances des applications managées. Ngen.exe crée des images natives, qui sont des fichiers contenant le code machine compilé spécifique au processeur, et les installe dans le cache des images natives sur l'ordinateur local. Le runtime peut utiliser des images natives du cache plutôt que le compilateur juste-à-temps (JIT) pour compiler l'assembly d'origine.
>
>à partir de [Ngen.exe (Native Image Generator)](https://msdn.microsoft.com/en-us/library/6t9t5wcf(v=vs.110).aspx)

Dans l’ordre de « ngen » un assembly, l’extension VSIX doit être installé « par instance par ordinateur ». Cela peut être activé en activant la case à cocher « tous les utilisateurs » dans le concepteur extension.vsixmanifest :

![Vérifiez tous les utilisateurs](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>L’activation de Ngen

Pour activer ngen pour un assembly, vous pouvez utiliser la **propriétés** fenêtre dans Visual Studio.

Il existe 4 propriétés qui peuvent être définies :

1. **Ngen** (booléenne) - si la valeur est true, le programme d’installation de Visual Studio est « ngen » de l’assembly.
2. **Application de Ngen** (chaîne), Ngen offre la possibilité d’utiliser le fichier app.config de l’application afin de résoudre les dépendances d’assembly. Cette valeur doit être définie à une application dont vous souhaitez utiliser (relatif au répertoire d’installation de Visual Studio) de app.config.
3. **Architecture de Ngen** (enum) - l’architecture de votre assembly de la compilation en mode natif. Les options sont : un. NotSpecified b. X86 c. X64 d. Tous
4. **Priorité de Ngen** (nombre entier compris entre 1 et 3) - décrite au niveau de la priorité de Ngen [les niveaux de priorité de Ngen.exe](https://msdn.microsoft.com/en-us/library/6t9t5wcf(v=vs.110).aspx#Anchor_3).

Voici un aperçu de la **propriétés** fenêtre en action :

![Ngen dans les propriétés](media/ngen-in-properties.png)

Cette opération ajoute des métadonnées à la référence de projet à l’intérieur du fichier .csproj du projet VSIX :

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

 >**Remarque :** vous pouvez modifier le fichier .csproj directement, si vous préférez.

## <a name="extra-information"></a>Informations supplémentaires

Les modifications concepteur des propriétés s’appliquent aux plus que les références de projet ; Vous pouvez définir les métadonnées de Ngen pour les éléments à l’intérieur de votre projet (en utilisant les mêmes méthodes décrites ci-dessus) aussi longtemps que les éléments sont des assemblys .NET.