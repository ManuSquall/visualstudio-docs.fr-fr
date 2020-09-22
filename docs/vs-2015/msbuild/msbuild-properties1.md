---
title: Properties1 MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- MSBuild, properties
ms.assetid: 962912ac-8931-49bf-a88c-0200b6e37362
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2399ff36639732f20babef368a1d9e2f6758a1c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839838"
---
# <a name="msbuild-properties1"></a>Properties1 MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les propriétés sont des paires nom-valeur qui peuvent être utilisées pour configurer des générations. Elles sont utiles pour transmettre des valeurs aux tâches, évaluer des conditions et stocker les valeurs qui seront référencées dans tout le fichier projet.  
  
## <a name="defining-and-referencing-properties-in-a-project-file"></a>Définition et référencement des propriétés dans un fichier projet  
 Les propriétés sont déclarées en créant un élément portant le nom de la propriété comme enfant d’un élément [PropertyGroup](../msbuild/propertygroup-element-msbuild.md). Par exemple, le code XML suivant crée une propriété nommée `BuildDir` pourvue de la valeur `Build`.  
  
```  
<PropertyGroup>  
    <BuildDir>Build</BuildDir>  
</PropertyGroup>  
```  
  
 Les propriétés sont référencées dans tout le fichier projet à l’aide de la syntaxe $(`PropertyName`). Par exemple, la propriété indiquée dans l’exemple précédent est référencée à l’aide de $(BuildDir).  
  
 La valeur d’une propriété peut être modifiée en redéfinissant la propriété. Une nouvelle valeur peut être octroyée à la propriété `BuildDir` en utilisant ce code XML :  
  
```  
<PropertyGroup>  
    <BuildDir>Alternate</BuildDir>  
</PropertyGroup>  
```  
  
 Les propriétés sont évaluées dans l’ordre dans lequel elles apparaissent dans le fichier projet. La nouvelle valeur de la propriété `BuildDir` doit être déclarée après que l’ancienne valeur a été affectée.  
  
## <a name="reserved-properties"></a>Propriétés réservées  
 MSBuild réserve certains noms de propriété pour stocker des informations sur le fichier projet et les binaires de MSBuild. Ces propriétés sont référencées avec la notation $ comme toute autre propriété. Par exemple, $(MSBuildProjectFile) retourne le nom de fichier complet du fichier projet, y compris l’extension de nom de fichier.  
  
 Pour plus d’informations, consultez les articles [Comment : référencer le nom ou l’emplacement du fichier projet](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md) et [Propriétés réservées et connues de MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md).  
  
## <a name="environment-properties"></a>Propriétés d’environnement  
 Vous pouvez référencer des variables d’environnement des fichiers projet de la même façon que les propriétés réservées. Par exemple, pour utiliser la variable d’environnement `PATH` dans votre fichier projet, utilisez $(Path). Si le projet contient une définition de propriété qui porte le même nom qu’une propriété d’environnement, la propriété du projet remplace la valeur de la variable d’environnement.  
  
 Chaque projet MSBuild dispose d’un bloc environnement isolé : il voit seulement les lectures et écritures de son propre bloc.  MSBuild lit uniquement les variables d’environnement lors de l’initialisation de la collection de propriétés, avant que le fichier projet ne soit évalué ou généré. À l’issue de cette opération, les propriétés d’environnement sont statiques. Autrement dit, chaque outil généré commence par les mêmes noms et valeurs.  
  
 Pour obtenir la valeur actuelle des variables d’environnement à partir d’un outil généré, utilisez les [fonctions de propriétés](../msbuild/property-functions.md) System.Environment.GetEnvironmentVariable. La méthode préférée est cependant d’utiliser le paramètre de tâche <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A>. Les propriétés d’environnement définies dans ce tableau de chaînes peuvent être transmises à l’outil généré sans affecter les variables d’environnement système.  
  
> [!TIP]
> Toutes les variables d’environnement ne sont pas lues pour devenir des propriétés initiales. Une variable d’environnement dont le nom n’est pas un nom de propriété MSBuild valide, par exemple « 386 », est ignoré.  
  
 Pour plus d’informations, consultez l’article [Comment : utiliser des variables d’environnement dans une génération](../msbuild/how-to-use-environment-variables-in-a-build.md).  
  
## <a name="registry-properties"></a>Propriétés de Registre  
 Vous pouvez lire les valeurs du Registre système à l’aide de la syntaxe suivante, où `Hive` est la ruche du Registre (par exemple, HKEY_LOCAL_MACHINE), `Key` le nom de la clé, `SubKey` le nom de la sous-clé, et `Value` la valeur de la sous-clé.  
  
```  
$(registry:Hive\MyKey\MySubKey@Value)  
```  
  
 Pour obtenir la valeur de la sous-clé par défaut, omettez la `Value`.  
  
```  
$(registry:Hive\MyKey\MySubKey)  
```  
  
 Cette valeur du Registre peut être utilisée pour initialiser une propriété de génération. Par exemple, pour créer une propriété de génération qui représente la page d’accueil Visual Studio Web Browser, utilisez ce code :  
  
```  
<PropertyGroup>  
  <VisualStudioWebBrowserHomePage>  
    $(registry:HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\12.0\WebBrowser@HomePage)  
  </VisualStudioWebBrowserHomePage>  
<PropertyGroup>  
```  
  
## <a name="global-properties"></a>Propriétés globales  
 MSBuild vous permet de définir des propriétés sur la ligne de commande à l’aide du commutateur **/property** (ou **/p**). Les valeurs de ces propriétés globales remplacent les valeurs de propriétés qui sont définies dans le fichier projet. Cela inclut les propriétés d’environnement, mais pas les propriétés réservées, qui ne peuvent pas être modifiées.  
  
 L’exemple suivant définit la propriété globale `Configuration` sur `DEBUG`.  
  
```  
msbuild.exe MyProj.proj /p:Configuration=DEBUG  
```  
  
 Les propriétés globales peuvent également être définies ou modifiées pour les projets enfants d’une génération multiprojet à l’aide de l’attribut `Properties` de la tâche MSBuild. Pour plus d’informations, consultez l’article [Tâche MSBuild](../msbuild/msbuild-task.md).  
  
 Si vous spécifiez une propriété à l’aide de l’attribut `TreatAsLocalProperty` dans une balise de projet, la valeur de cette propriété globale ne remplace pas la valeur de propriété définie dans le fichier projet. Pour plus d’informations, consultez les articles [Project, élément (MSBuild)](../msbuild/project-element-msbuild.md) et [Comment : générer les mêmes fichiers sources avec des options différentes](../msbuild/how-to-build-the-same-source-files-with-different-options.md).  
  
## <a name="property-functions"></a>Fonctions de propriétés  
 Depuis .NET Framework version 4, vous pouvez utiliser les fonctions de propriétés pour évaluer vos scripts MSBuild. Vous pouvez lire l’heure système, comparer des chaînes, établir des correspondances avec des expressions régulières et effectuer d’autres actions dans votre script de génération sans utiliser de tâches MSBuild.  
  
 Vous pouvez utiliser des méthodes chaîne (instance) sur toute valeur de propriété, et vous pouvez appeler les méthodes statiques de nombreuses classes système. Par exemple, vous pouvez définir une propriété de génération à la date du jour comme suit.  
  
```  
<Today>$([System.DateTime]::Now.ToString("yyyy.MM.dd"))</Today>  
```  
  
 Pour plus d’informations et pour obtenir la liste des fonctions de propriétés, consultez l’article [Fonctions de propriétés](../msbuild/property-functions.md).  
  
## <a name="creating-properties-during-execution"></a>Création de propriétés pendant l’exécution  
 Des valeurs sont attribuées aux propriétés situées en dehors des éléments `Target` pendant la phase d’évaluation d’une génération. Pendant la phase d’exécution suivante, des propriétés peuvent être créées ou modifiées en procédant comme suit :  
  
- Une propriété peut être émise par une tâche quelconque. Pour émettre une propriété, l’élément [Task](../msbuild/task-element-msbuild.md) doit posséder un élément [Output](../msbuild/output-element-msbuild.md) enfant pourvu d’un attribut `PropertyName`.  
  
- Une propriété peut être émise par la tâche [CreateProperty](../msbuild/createproperty-task.md). Cette utilisation est dépréciée.  
  
- Depuis .NET Framework 3.5, les éléments `Target` peuvent contenir des éléments `PropertyGroup`, qui peuvent comporter des déclarations de propriété.  
  
## <a name="storing-xml-in-properties"></a>Stockage de code XML dans les propriétés  
 Les propriétés peuvent contenir un code XML arbitraire, ce qui peut aider à transmettre des valeurs aux tâches ou à afficher les informations de journalisation. L’exemple suivant présente la propriété `ConfigTemplate`, qui est pourvue d’une valeur qui contient le code XML et d’autres références de propriété. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] remplace les références de propriété par leurs valeurs de propriété respectives. Les valeurs de propriété sont attribuées dans l’ordre dans lequel elles apparaissent. Par conséquent, dans cet exemple, les propriétés `$(MySupportedVersion)`, `$(MyRequiredVersion)` et `$(MySafeMode)` doivent déjà avoir été définies.  
  
```  
  
<PropertyGroup>  
    <ConfigTemplate>  
        <Configuration>  
            <Startup>  
                <SupportedRuntime  
                    ImageVersion="$(MySupportedVersion)"  
                    Version="$(MySupportedVersion)"/>  
                <RequiredRuntime  
                    ImageVersion="$(MyRequiredVersion)  
                    Version="$(MyRequiredVersion)"  
                    SafeMode="$(MySafeMode)"/>  
            </Startup>  
        </Configuration>  
    </ConfigTemplate>  
</PropertyGroup>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts MSBuild](../msbuild/msbuild-concepts.md)  
 [MSBuild](msbuild.md)  
 [Comment : utiliser des variables d’environnement dans une build](../msbuild/how-to-use-environment-variables-in-a-build.md)   
 [Comment : référencer le nom ou l’emplacement du fichier projet](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md)   
 [Comment : générer les mêmes fichiers sources avec des options différentes](../msbuild/how-to-build-the-same-source-files-with-different-options.md)   
 [Propriétés réservées et connues de MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)   
 [Property, élément (MSBuild)](../msbuild/property-element-msbuild.md)
