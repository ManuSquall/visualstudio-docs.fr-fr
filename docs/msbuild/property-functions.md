---
title: Fonctions de propriétés | Microsoft Docs
description: Découvrez comment utiliser les fonctions de propriété, qui sont des appels à .NET Framework méthodes qui apparaissent dans les définitions de propriété MSBuild.
ms.custom: SEO-VS-2020
ms.date: 02/21/2017
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, property functions
ms.assetid: 2253956e-3ae0-4bdc-9d3a-4881dfae4ddb
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4c1e7a90d5d037865d9942ea1b91f33d7724706f
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048816"
---
# <a name="property-functions"></a>Fonctions de propriétés

Les fonctions de propriété sont des appels à .NET Framework méthodes qui s’affichent dans les définitions de propriété MSBuild. Au contraire des tâches, les fonctions de propriété peuvent être utilisées en dehors des cibles et elles sont évaluées avant l'exécution des cibles.

Sans utiliser de tâches MSBuild, vous pouvez lire l'heure système, comparer des chaînes, établir des correspondances avec des expressions régulières et effectuer d'autres actions dans votre script de génération. MSBuild tente de convertir les chaînes en nombres et les nombres en chaînes, et d'effectuer les autres conversions nécessaires.

Les valeurs de chaîne retournées à partir de fonctions de propriété ont des [caractères spéciaux](msbuild-special-characters.md) d’échappement. Si vous souhaitez que la valeur soit traitée comme si elle avait été placée directement dans le fichier projet, utilisez `$([MSBuild]::Unescape())` pour éliminer les caractères spéciaux d’échappement.

Les fonctions de propriété sont disponibles avec .NET Framework 4 et versions ultérieures.

## <a name="property-function-syntax"></a>Syntaxe des fonctions de propriété

Il y a trois sortes de fonctions de propriété. Chaque fonction a une syntaxe différente :

- Fonctions de propriété (d'instance) de chaîne
- Fonctions de propriété statique
- Fonctions de propriété MSBuild

### <a name="string-property-functions"></a>Fonctions de propriété de type chaîne

Toutes les valeurs de propriété de build sont simplement des valeurs de chaîne. Vous pouvez utiliser des méthodes (d'instance) de chaîne pour effectuer des opérations sur toutes les valeurs de propriété. Par exemple, vous pouvez extraire le nom du lecteur (les trois premiers caractères) d’une propriété de build qui représente un chemin d’accès complet à l’aide de ce code :

```
$(ProjectOutputFolder.Substring(0,3))
```

### <a name="static-property-functions"></a>Fonctions de propriété statique

Dans votre script de génération, vous pouvez accéder aux propriétés et aux méthodes statiques de nombreuses classes système. Pour obtenir la valeur d’une propriété statique, utilisez la syntaxe suivante, où \<Class> est le nom de la classe système et \<Property> est le nom de la propriété.

```
$([Class]::Property)
```

Par exemple, vous pouvez utiliser le code suivant pour définir une propriété de build avec la date et l'heure actuelles.

```xml
<Today>$([System.DateTime]::Now)</Today>
```

Pour appeler une méthode statique, utilisez la syntaxe suivante, où \<Class> est le nom de la classe système, \<Method> est le nom de la méthode et ( \<Parameters> ) est la liste de paramètres de la méthode :

```
$([Class]::Method(Parameters))
```

Par exemple, pour définir une propriété de build avec un nouveau GUID, vous pouvez utiliser ce script :

```xml
<NewGuid>$([System.Guid]::NewGuid())</NewGuid>
```

Dans les fonctions de propriété statique, vous pouvez utiliser toutes les méthodes ou propriétés statiques de ces classes système :

- <xref:System.Byte?displayProperty=nameWithType>
- <xref:System.Char?displayProperty=nameWithType>
- <xref:System.Convert?displayProperty=nameWithType>
- <xref:System.DateTime?displayProperty=nameWithType>
- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Double?displayProperty=nameWithType>
- <xref:System.Enum?displayProperty=nameWithType>
- <xref:System.Guid?displayProperty=nameWithType>
- <xref:System.Int16?displayProperty=nameWithType>
- <xref:System.Int32?displayProperty=nameWithType>
- <xref:System.Int64?displayProperty=nameWithType>
- <xref:System.IO.Path?displayProperty=nameWithType>
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.OSPlatform?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation?displayProperty=nameWithType>
- <xref:System.UInt16?displayProperty=nameWithType>
- <xref:System.UInt32?displayProperty=nameWithType>
- <xref:System.UInt64?displayProperty=nameWithType>
- <xref:System.SByte?displayProperty=nameWithType>
- <xref:System.Single?displayProperty=nameWithType>
- <xref:System.String?displayProperty=nameWithType>
- <xref:System.StringComparer?displayProperty=nameWithType>
- <xref:System.TimeSpan?displayProperty=nameWithType>
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>
- <xref:System.UriBuilder?displayProperty=nameWithType>
- <xref:System.Version?displayProperty=nameWithType>
- <xref:Microsoft.Build.Utilities.ToolLocationHelper?displayProperty=nameWithType>

Vous pouvez également utiliser les méthodes et propriétés statiques suivantes :

- [System.Environment::CommandLine](xref:System.Environment.CommandLine*)
- [System.Environment::ExpandEnvironmentVariables](xref:System.Environment.ExpandEnvironmentVariables*)
- [System. Environment :: GetEnvironmentVariable](xref:System.Environment.GetEnvironmentVariable*)
- [System.Environment::GetEnvironmentVariables](xref:System.Environment.GetEnvironmentVariables*)
- [System.Environment::GetFolderPath](xref:System.Environment.GetFolderPath*)
- [System.Environment::GetLogicalDrives](xref:System.Environment.GetLogicalDrives*)
- [System.IO.Directory::GetDirectories](xref:System.IO.Directory.GetDirectories*)
- [System.IO.Directory::GetFiles](xref:System.IO.Directory.GetFiles*)
- [System.IO.Directory::GetLastAccessTime](xref:System.IO.Directory.GetLastAccessTime*)
- [System.IO.Directory::GetLastWriteTime](xref:System.IO.Directory.GetLastWriteTime*)
- [System.IO.Directory::GetParent](xref:System.IO.Directory.GetParent*)
- [System.IO.File::Exists](xref:System.IO.File.Exists*)
- [System. IO. file :: GetCreationTime](xref:System.IO.File.GetCreationTime*)
- [System. IO. file :: GetAttributes](xref:System.IO.File.GetAttributes*)
- [System. IO. file :: GetLastAccessTime](xref:System.IO.File.GetLastAccessTime*)
- [System. IO. file :: GetLastWriteTime](xref:System.IO.File.GetLastWriteTime*)
- [System.IO.File::ReadAllText](xref:System.IO.File.ReadAllText*)

### <a name="calling-instance-methods-on-static-properties"></a>Appeler des méthodes d’instance sur des propriétés statiques

Si vous accédez à une propriété statique qui retourne une instance d'un objet, vous pouvez appeler les méthodes d'instance de cet objet. Pour appeler une méthode d’instance, utilisez la syntaxe suivante, où \<Class> est le nom de la classe système, \<Property> est le nom de la propriété, \<Method> est le nom de la méthode et ( \<Parameters> ) est la liste des paramètres de la méthode :

```
$([Class]::Property.Method(Parameters))
```

Le nom de la classe doit être complet avec l'espace de noms.

Par exemple, vous pouvez utiliser le code suivant pour définir une propriété de build avec la date du jour.

```xml
<Today>$([System.DateTime]::Now.ToString('yyyy.MM.dd'))</Today>
```

### <a name="msbuild-property-functions"></a>Fonctions de propriété MSBuild

Vous pouvez accéder à plusieurs méthodes statiques dans votre build, qui prennent en charge des fonctions liées à l'arithmétique, à la logique au niveau du bit et aux caractères d'échappement. Vous accédez à ces méthodes en utilisant la syntaxe suivante, où \<Method> est le nom de la méthode et ( \<Parameters> ) est la liste des paramètres de la méthode.

```
$([MSBuild]::Method(Parameters))
```

Par exemple, pour ajouter en même temps deux propriétés qui ont des valeurs numériques, utilisez le code suivant.

```
$([MSBuild]::Add($(NumberOne), $(NumberTwo)))
```

Voici une liste de fonctions de propriété MSBuild :

|Signature de fonction|Description|
|------------------------|-----------------|
|double Add(double a, double b)|Additionne deux doubles.|
|long Add(long a, long b)|Additionne deux longs.|
|double Subtract(double a, double b)|Fait une soustraction entre deux doubles.|
|long Subtract(long a, long b)|Fait une soustraction entre deux longs.|
|double Multiply(double a, double b)|Fait une multiplication de deux doubles.|
|long Multiply(long a, long b)|Fait une multiplication de deux longs.|
|double Divide(double a, double b)|Fait une division de deux doubles.|
|long Divide(long a, long b)|Fait une division de deux longs.|
|double Modulo(double a, double b)|Calcule le modulo de deux doubles.|
|long Modulo(long a, long b)|Calcule le modulo de deux longs.|
|chaîne Escape(chaîne sans caractère d'échappement)|Place un caractère d'échappement devant la chaîne selon les règles d'échappement de MSBuild.|
|chaîne Unescape(chaîne avec caractère d'échappement)|Enlève le caractère d'échappement de la chaîne selon les règles d'échappement de MSBuild.|
|entier BitwiseOr(entier premier, entier second)|Effectue un `OR` au niveau du bit sur le premier et le second entier (premier &#124; second).|
|entier BitwiseAnd(entier premier, entier second)|Effectue un `AND` au niveau du bit sur le premier et le second entier (premier & second).|
|entier BitwiseXor(entier premier, entier second)|Effectue un `XOR` au niveau du bit sur le premier et le second entier (premier ^ second).|
|entier BitwiseNot(entier premier)|Effectue un `NOT` au niveau du bit (~premier).|
|bool IsOsPlatform(string platformString)|Spécifie si la plateforme du système d’exploitation actuelle est `platformString`. `platformString`doit être membre de <xref:System.Runtime.InteropServices.OSPlatform>.|
|bool IsOSUnixLike()|True si le système d’exploitation actuel est un système Unix.|
|string NormalizePath(params string[] path)|Obtient le chemin complet au format canonique du chemin fourni et vérifie qu’il contient les caractères de séparateur de répertoire appropriés au système d’exploitation actuel.|
|string NormalizeDirectory(params string[] path)|Obtient le chemin complet au format canonique du répertoire fourni et vérifie qu’il contient les caractères de séparateur de répertoire appropriés au système d’exploitation actuel et qu’il se termine par une barre oblique.|
|string EnsureTrailingSlash(string path)|Si le chemin donné ne se termine pas par une barre oblique, ajoutez-en une. Si le chemin est une chaîne vide, ne le modifiez pas.|
|string GetPathOfFileAbove(string file, string startingDirectory)|Recherche et retourne le chemin d’accès complet à un fichier dans la structure de répertoires au-dessus de l’emplacement du fichier de build actuel, ou basé sur `startingDirectory` , s’il est spécifié.|
|GetDirectoryNameOfFileAbove(string startingDirectory, string fileName)|Recherchez et retournez le répertoire d’un fichier dans le répertoire spécifié ou un emplacement dans la structure de répertoires au-dessus de ce répertoire.|
|string MakeRelative(string basePath, string path)|Rend `path` relatif à `basePath`. `basePath` doit être un répertoire absolu. Si rendre `path` relatif n’est pas possible, il est retourné sous forme de chaîne textuelle. Semblable à `Uri.MakeRelativeUri`.|
|string ValueOrDefault(string conditionValue, string defaultValue)|Retourne la chaîne dans le paramètre 'defaultValue' seulement si le paramètre 'conditionValue' est vide ; sinon, retourne la valeur conditionValue.|

## <a name="nested-property-functions"></a>Fonctions de propriété imbriquées

Vous pouvez combiner des fonctions de propriété pour former des fonctions plus complexes, comme dans l'exemple suivant.

```
$([MSBuild]::BitwiseAnd(32, $([System.IO.File]::GetAttributes(tempFile))))
```

Cet exemple retourne le bit <xref:System.IO.FileAttributes> de `Archive` (32 ou 0) du fichier spécifié par le chemin d'accès `tempFile`. Notez que les valeurs des données énumérées ne peuvent pas apparaître par leur nom dans les fonctions de propriété. La valeur numérique (32) doit être utilisée à la place.

Des métadonnées peuvent également apparaître dans des fonctions de propriété imbriquées. Pour plus d’informations, consultez l’article [Batching (Traitement par lot MSBuild)](../msbuild/msbuild-batching.md).

## <a name="msbuild-doestaskhostexist"></a>Fonction MSBuild DoesTaskHostExist

La fonction de propriété `DoesTaskHostExist` de MSBuild retourne une valeur indiquant si un hôte de tâche est actuellement installé pour les valeurs de runtime et d'architecture spécifiées.

La syntaxe de cette fonction de propriété est la suivante :

```
$([MSBuild]::DoesTaskHostExist(string theRuntime, string theArchitecture))
```

## <a name="msbuild-ensuretrailingslash"></a>MSBuild EnsureTrailingSlash

La fonction de propriété `EnsureTrailingSlash` dans MSBuild ajoute une barre oblique de fin s’il n’en existe pas déjà une.

La syntaxe de cette fonction de propriété est la suivante :

```
$([MSBuild]::EnsureTrailingSlash('$(PathProperty)'))
```

## <a name="msbuild-getdirectorynameoffileabove"></a>Fonction MSBuild GetDirectoryNameOfFileAbove

La fonction de propriété MSBuild `GetDirectoryNameOfFileAbove` recherche un fichier dans les répertoires situés sous le répertoire actif du chemin d'accès.

 La syntaxe de cette fonction de propriété est la suivante :

```
$([MSBuild]::GetDirectoryNameOfFileAbove(string ThePath, string TheFile))
```

 Le code suivant est un exemple de cette syntaxe.

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))\EnlistmentInfo.props" Condition=" '$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))' != '' " />
```

## <a name="msbuild-getpathoffileabove"></a>MSBuild GetPathOfFileAbove

La `GetPathOfFileAbove` fonction de propriété dans MSBuild retourne le chemin d’accès du fichier spécifié, s’il se trouve dans la structure de répertoires au-dessus du répertoire actif. Sur le plan fonctionnel, elle revient à appeler

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />
```

La syntaxe de cette fonction de propriété est la suivante :

```
$([MSBuild]::GetPathOfFileAbove(dir.props))
```

## <a name="msbuild-getregistryvalue"></a>Fonction MSBuild GetRegistryValue

La propriété de fonction MSBuild `GetRegistryValue` retourne la valeur d'une clé de Registre. Cette fonction prend deux arguments, le nom de la clé et le nom de la valeur, et retourne la valeur qui se trouve dans le Registre. Si vous ne spécifiez pas un nom de valeur, la valeur par défaut est retournée.

Les exemples suivants montrent comment cette fonction est utilisée :

```
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, ``))                                  // default value
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, `SymbolCacheDir`))
$([MSBuild]::GetRegistryValue(`HKEY_LOCAL_MACHINE\SOFTWARE\(SampleName)`, `(SampleValue)`))             // parens in name and value
```

## <a name="msbuild-getregistryvaluefromview"></a>Fonction MSBuild GetRegistryValueFromView

La fonction de propriété MSBuild `GetRegistryValueFromView` extrait des données du Registre système en fonction de la clé de Registre, de la valeur et d'une ou plusieurs vues ordonnées du Registre. La clé et la valeur sont recherchées dans chaque vue du Registre dans l'ordre, jusqu'à ce qu'elles soient trouvées.

Le syntaxe de cette fonction de propriété est :

```
[MSBuild]::GetRegistryValueFromView(string keyName, string valueName, object defaultValue, params object[] views)
```

Le système d’exploitation Windows 64 bits gère une clé de Registre **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node** qui présente une **HKEY_LOCAL_MACHINE\SOFTWARE** vue de registre pour les applications 32 bits.

Par défaut, une application 32 bits s'exécutant sur WOW64 accède à la vue de Registre 32 bits et une application 64 bits accède à la vue de Registre 64 bits.

Les vues de Registre suivantes sont disponibles :

|Vue de Registre|Définition|
|-------------------|----------------|
|RegistryView.Registry32|Vue de Registre pour les applications 32 bits.|
|RegistryView.Registry64|Vue de Registre pour les applications 64 bits.|
|RegistryView.Default|La vue de Registre qui correspond au processus sur lequel l'application s'exécute.|

Voici un exemple.

 ```
$([MSBuild]::GetRegistryValueFromView('HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SDKs\Silverlight\v3.0\ReferenceAssemblies', 'SLRuntimeInstallPath', null, RegistryView.Registry64, RegistryView.Registry32))
```

Obtient les données **SLRuntimeInstallPath** de la clé **ReferenceAssemblies** , en recherchant d’abord dans la vue de Registre 64 bits, puis dans la vue de Registre 32 bits.

## <a name="msbuild-makerelative"></a>Fonction MSBuild MakeRelative

La fonction de propriété MSBuild `MakeRelative` retourne le chemin d'accès relatif du second chemin par rapport au premier chemin. Chaque chemin peut être un fichier ou un dossier.

La syntaxe de cette fonction de propriété est la suivante :

```
$([MSBuild]::MakeRelative($(FileOrFolderPath1), $(FileOrFolderPath2)))
```

Le code suivant est un exemple de cette syntaxe.

```xml
<PropertyGroup>
    <Path1>c:\users\</Path1>
    <Path2>c:\users\username\</Path2>
</PropertyGroup>

<Target Name = "Go">
    <Message Text ="$([MSBuild]::MakeRelative($(Path1), $(Path2)))" />
    <Message Text ="$([MSBuild]::MakeRelative($(Path2), $(Path1)))" />
</Target>

<!--
Output:
   username\
   ..\
-->
```

## <a name="msbuild-valueordefault"></a>Fonction MSBuild ValueOrDefault

La fonction de propriété MSBuild `ValueOrDefault` retourne le premier argument, sauf s'il est null ou vide. Si le premier argument est null ou vide, la fonction retourne le second argument.

L'exemple suivant montre comment cette fonction est utilisée.

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <Value1>$([MSBuild]::ValueOrDefault('$(UndefinedValue)', 'a'))</Value1>
        <Value2>$([MSBuild]::ValueOrDefault('b', '$(Value1)'))</Value2>
    </PropertyGroup>

    <Target Name="MyTarget">
        <Message Text="Value1 = $(Value1)" />
        <Message Text="Value2 = $(Value2)" />
    </Target>
</Project>

<!--
Output:
  Value1 = a
  Value2 = b
-->
```

## <a name="msbuild-condition-functions"></a>Fonctions de condition MSBuild

Les fonctions `Exists` et ne `HasTrailingSlash` sont pas des fonctions de propriété. Elles peuvent être utilisées avec l' `Condition` attribut. Consultez les [Conditions MSBuild](msbuild-conditions.md).

## <a name="see-also"></a>Voir aussi

- [MSBuild (propriétés)](../msbuild/msbuild-properties.md)

- [Vue d’ensemble de MSBuild](../msbuild/msbuild.md)
