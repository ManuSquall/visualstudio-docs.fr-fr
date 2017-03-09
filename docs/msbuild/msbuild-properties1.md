---
title: "MSBuild Properties1 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, propriétés"
ms.assetid: 962912ac-8931-49bf-a88c-0200b6e37362
caps.latest.revision: 32
caps.handback.revision: 32
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MSBuild Properties1
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les propriétés sont des paires nom-valeur qui peuvent être utilisés pour configurer les générations. Elles sont utiles pour passer des valeurs aux tâches, évaluer des conditions et stocker des valeurs qui seront référencées dans tout le fichier projet.  
  
## <a name="defining-and-referencing-properties-in-a-project-file"></a>Définir et référencer les propriétés dans un fichier de projet  
 Les propriétés sont déclarées en créant un élément qui porte le nom de la propriété comme enfant d’un [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) élément. Par exemple, le code XML suivant crée une propriété nommée `BuildDir` qui a la valeur `Build`.  
  
```  
<PropertyGroup>  
    <BuildDir>Build</BuildDir>  
</PropertyGroup>  
```  
  
 Dans le fichier projet, les propriétés sont référencées à l’aide de la syntaxe $(`PropertyName`). Par exemple, la propriété dans l’exemple précédent est référencée à l’aide de $(BuildDir).  
  
 Les valeurs de propriété peuvent être modifiées en redéfinissant la propriété. Le `BuildDir` une nouvelle valeur à l’aide de ce code XML peut être attribuée à propriété :  
  
```  
<PropertyGroup>  
    <BuildDir>Alternate</BuildDir>  
</PropertyGroup>  
```  
  
 Les propriétés sont évaluées dans l’ordre dans lequel ils apparaissent dans le fichier projet. La nouvelle valeur de `BuildDir` doit être déclarée après que l’ancienne valeur est affectée.  
  
## <a name="reserved-properties"></a>Propriétés réservées  
 MSBuild réserve certains noms de propriété pour stocker des informations sur le fichier projet et les binaires de MSBuild. Ces propriétés sont référencées à l’aide de la notation $, comme toute autre propriété. Par exemple, $ (MSBuildProjectFile) retourne le nom de fichier complet du fichier projet, y compris l’extension de nom de fichier.  
  
 Pour plus d’informations, consultez [Comment : référencer le nom ou l’emplacement du fichier projet](../Topic/How%20to:%20Reference%20the%20Name%20or%20Location%20of%20the%20Project%20File.md) et [réservé MSBuild et les propriétés connues](../msbuild/msbuild-reserved-and-well-known-properties.md).  
  
## <a name="environment-properties"></a>Propriétés d’environnement  
 Vous pouvez référencer des variables d’environnement dans les fichiers projet comme vous référencez les propriétés réservées. Par exemple, pour utiliser le `PATH` variable d’environnement dans votre fichier projet, utilisez $(Path). Si le projet contient une définition de propriété qui porte le même nom qu’une propriété de l’environnement, la propriété du projet substitue la valeur de la variable d’environnement.  
  
 Chaque projet MSBuild dispose d’un bloc d’environnement isolé : il seulement voit des lectures et les écrit dans son propre bloc.  MSBuild lit uniquement les variables d’environnement lors de l’initialisation de la collection de propriétés, avant que le fichier de projet soit évalué ou intégré. Après cela, les propriétés d’environnement sont statiques, autrement dit, chaque outil engendré démarre avec les mêmes noms et les valeurs.  
  
 Pour obtenir la valeur actuelle des variables d’environnement à partir d’un outil généré automatiquement, utilisez la [fonctions de propriété](../msbuild/property-functions.md) à System.Environment.GetEnvironmentVariable. La méthode recommandée, cependant, est d’utiliser le paramètre de tâche <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A>. Propriétés d’environnement définies dans ce tableau de chaînes peuvent être transmises à l’outil engendré sans affecter les variables d’environnement système.  
  
> [!TIP]
>  Pas toutes les variables d’environnement sont lues dans à devenir des propriétés initiales. Toute variable d’environnement dont le nom n’est pas un valide MSBuild noms de propriétés, telles que « 386 », est ignoré.  
  
 Pour plus d’informations, consultez [Comment : utiliser les Variables d’environnement dans une Build](../Topic/How%20to:%20Use%20Environment%20Variables%20in%20a%20Build.md).  
  
## <a name="registry-properties"></a>Propriétés du Registre  
 Vous pouvez lire les valeurs du Registre système à l’aide de la syntaxe suivante, où `Hive` est la ruche du Registre (par exemple, HKEY_LOCAL_MACHINE) `Key` est le nom de la clé `SubKey` est le nom de la sous-clé et `Value` est la valeur de la sous-clé.  
  
```  
$(registry:Hive\MyKey\MySubKey@Value)  
```  
  
 Pour obtenir la valeur de la sous-clé par défaut, omettez le `Value`.  
  
```  
$(registry:Hive\MyKey\MySubKey)  
```  
  
 Cette valeur de Registre peut être utilisée pour initialiser une propriété de build. Par exemple, pour créer une propriété de build qui représente la page d’accueil Visual Studio, utilisez ce code :  
  
```  
<PropertyGroup>  
  <VisualStudioWebBrowserHomePage>  
    $(registry:HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\12.0\WebBrowser@HomePage)  
  </VisualStudioWebBrowserHomePage>  
<PropertyGroup>  
```  
  
## <a name="global-properties"></a>Propriétés globales  
 MSBuild vous permet de définir des propriétés sur la ligne de commande à l’aide de la **cette propriété** (ou **/p**) basculer. Ces valeurs de propriété globales substituent les valeurs de propriété qui sont définies dans le fichier projet. Cela inclut les propriétés de l’environnement, mais n’inclut pas les propriétés réservées, qui ne peut pas être modifiées.  
  
 L’exemple suivant définit les paramètres globaux `Configuration` propriété `DEBUG`.  
  
```  
msbuild.exe MyProj.proj /p:Configuration=DEBUG  
```  
  
 Propriétés globales peuvent également être définies ou modifiées pour les projets enfants dans une build à projets multiples à l’aide de la `Properties` l’attribut de la tâche MSBuild. Pour plus d’informations, consultez [tâche MSBuild](../msbuild/msbuild-task.md).  
  
 Si vous spécifiez une propriété à l’aide de la `TreatAsLocalProperty` attribut dans une balise de projet, que la valeur de propriété globale ne remplace pas la valeur de propriété est définie dans le fichier projet. Pour plus d’informations, consultez [Project, élément (MSBuild)](../msbuild/project-element-msbuild.md) et [Comment : générer les mêmes fichiers sources avec des Options différentes](../msbuild/how-to-build-the-same-source-files-with-different-options.md).  
  
## <a name="property-functions"></a>Fonctions de propriétés  
 À compter de .NET Framework version 4, vous pouvez utiliser les fonctions de propriété pour évaluer vos scripts MSBuild. Vous pouvez lire l’heure système, comparer des chaînes, rechercher des expressions régulières et effectuer de nombreuses autres actions dans votre script de compilation sans utiliser de tâches MSBuild.  
  
 Vous pouvez utiliser les méthodes de chaîne (instance) de fonctionner sur n’importe quelle valeur de propriété, et vous pouvez appeler les méthodes statiques de nombreuses classes système. Par exemple, vous pouvez définir une propriété de build à la date du jour comme suit.  
  
```  
<Today>$([System.DateTime]::Now.ToString("yyyy.MM.dd"))</Today>  
```  
  
 Pour plus d’informations et une liste des fonctions de propriété, consultez [fonctions de propriété](../msbuild/property-functions.md).  
  
## <a name="creating-properties-during-execution"></a>Création de propriétés pendant l’exécution  
 Propriétés positionnées en dehors de `Target` valeurs sont assignées à éléments pendant la phase d’évaluation d’une build. Pendant la phase d’exécution suivante, les propriétés peuvent être créées ou modifiées comme suit :  
  
-   Une propriété peut être émise par n’importe quelle tâche. Pour émettre une propriété, le [tâche](../msbuild/task-element-msbuild.md) élément doit avoir un enfant [sortie](../msbuild/output-element-msbuild.md) élément ayant une `PropertyName` attribut.  
  
-   Une propriété peut être émise par le [CreateProperty](../msbuild/createproperty-task.md) tâche. Cette utilisation est déconseillée.  
  
-   À compter de .NET Framework 3.5, `Target` peuvent contenir des éléments `PropertyGroup` éléments pouvant contenir des déclarations de propriété.  
  
## <a name="storing-xml-in-properties"></a>Stockage XML dans les propriétés  
 Propriétés peuvent contenir un code XML arbitraire, qui peut aider à passer des valeurs aux tâches ou à afficher des informations de journalisation. L’exemple suivant illustre le `ConfigTemplate` propriété, qui a une valeur qui contient le XML et autres propriétés références. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] remplace les références de propriété par leurs valeurs de propriété respectives. Les valeurs de propriété sont assignées dans l’ordre dans lequel ils apparaissent. Par conséquent, dans cet exemple, `$(MySupportedVersion)`, `$(MyRequiredVersion)`, et `$(MySafeMode)` doivent avoir été déjà définis.  
  
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
 [MSBuild](../msbuild/msbuild1.md)  
 [Comment : utiliser des Variables d’environnement dans une génération](../Topic/How%20to:%20Use%20Environment%20Variables%20in%20a%20Build.md)   
 [Comment : référencer le nom ou l’emplacement du fichier projet](../Topic/How%20to:%20Reference%20the%20Name%20or%20Location%20of%20the%20Project%20File.md)   
 [Comment : générer les mêmes fichiers sources avec des Options différentes](../msbuild/how-to-build-the-same-source-files-with-different-options.md)   
 [MSBuild, propriétés réservées et connues](../msbuild/msbuild-reserved-and-well-known-properties.md)   
 [Property, élément (MSBuild)](../msbuild/property-element-msbuild.md)