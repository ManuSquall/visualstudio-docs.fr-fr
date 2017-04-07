---
title: Prise en charge de NGen dans VSIX v3 | Documents Microsoft
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
caps.latest.revision: 1
author: gregvanl
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 46b6f4d13b4c1938797dbe6cf6023e3c8c42d1ed
ms.lasthandoff: 03/07/2017

---
# <a name="ngen-support-in-vsix-v3"></a>Prise en charge de NGen dans VSIX v3

Avec Visual Studio 2017 et le nouveau v3 VSIX (version 3) manifeste d’extension format, extension les développeurs peuvent désormais « ngen » leurs assemblys au moment de l’installation.

Voici un extrait de MSDN expliquant quel « ngen » est :

>L'outil Native Image Generator Tool (Ngen.exe) est un outil qui améliore les performances des applications managées. Ngen.exe crée des images natives, qui sont des fichiers contenant le code machine compilé spécifique au processeur, et les installe dans le cache des images natives sur l'ordinateur local. Le runtime peut utiliser des images natives du cache plutôt que le compilateur juste-à-temps (JIT) pour compiler l'assembly d'origine.
>
>à partir de [Ngen.exe (Native Image Generator)](https://msdn.microsoft.com/en-us/library/6t9t5wcf(v=vs.110).aspx)

Dans l’ordre à « ngen » un assembly, l’extension VSIX doit être installé « par instance par ordinateur ». Cela peut être activée en cochant la case « tous les utilisateurs » dans le concepteur extension.vsixmanifest :

![Vérifiez tous les utilisateurs](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>L’activation de Ngen

Pour activer ngen pour un assembly, vous pouvez utiliser la **propriétés** fenêtre dans Visual Studio.

Il existe 4 propriétés qui peuvent être définies :

1. **Ngen** (booléen) : si la valeur est true, le programme d’installation de Visual Studio sera « ngen » de l’assembly.
2. **Application de Ngen** (chaîne) – Ngen offre la possibilité d’utiliser le fichier app.config de l’application afin de résoudre les dépendances d’assembly. Cette valeur doit être définie à une application dont vous souhaitez utiliser (par rapport au répertoire d’installation Visual Studio) de app.config.
3. **Architecture de Ngen** (enum) – l’architecture en mode natif compile votre assembly. Les options sont : un. B NotSpecified. X86 c. X64 d. Tout
4. **Priorité de Ngen** (nombre entier compris entre 1 et 3) – documenté au niveau de la priorité de Ngen [niveaux de priorité Ngen.exe](https://msdn.microsoft.com/en-us/library/6t9t5wcf(v=vs.110).aspx#Anchor_3).

Voici un aperçu de la **propriétés** fenêtre en action :

![Ngen dans les propriétés](media/ngen-in-properties.png)

Cette opération ajoute des métadonnées à la référence de projet à l’intérieur de l’extension VSIX fichier .csproj :

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

Les modifications apportées aux propriétés concepteur s’appliquent aux plus que les références de projet ; Vous pouvez définir les métadonnées de Ngen pour les éléments à l’intérieur de votre projet (en utilisant les mêmes méthodes décrites ci-dessus) aussi longtemps que les éléments sont des assemblys .NET.
