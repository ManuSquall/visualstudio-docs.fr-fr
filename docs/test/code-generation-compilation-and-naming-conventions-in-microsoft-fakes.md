---
title: "Génération, compilation de code et conventions de nommage dans Microsoft Fakes | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 20221de4-2a9e-4787-b99a-b5855bb90872
caps.latest.revision: "16"
ms.author: douge
manager: douge
ms.workload: multiple
ms.openlocfilehash: e293d6ef200fec89150d76d94233bb171374a1d9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="code-generation-compilation-and-naming-conventions-in-microsoft-fakes"></a>Génération et compilation de code et conventions de nommage dans Microsoft Fakes
Cette rubrique traite des options et des problèmes dans la génération et la compilation de code Fakes, et décrit les conventions de nommage pour les types Fakes générés, les membres et les paramètres.  
  
 **Spécifications**  
  
-   Visual Studio Enterprise  
  
##  <a name="BKMK_In_this_topic"></a> Dans cette rubrique  
  
-   [Génération et compilation de code](#BKMK_Code_generation_and_compilation)  
  
-   [Configuration de la génération du code des stubs](#BKMK_Configuring_code_generation_of_stubs)
  
-   [Filtrage de types](#BKMK_Type_filtering)
  
-   [Classes concrètes et méthodes virtuelles d’opérations stub](#BKMK_Stubbing_concrete_classes_and_virtual_methods)
  
-   [Types internes](#BKMK_Internal_types)
  
-   [Optimisation de la durée de génération](#BKMK_Optimizing_build_times)
  
-   [Prévention du conflit de nom d’assembly](#BKMK_Avoiding_assembly_name_clashing)  
  
-   [Conventions d’affectation de noms Fakes](#BKMK_Fakes_naming_conventions)  
  
-   [Conventions de nommage du type shim et du type stub](#BKMK_Shim_type_and_stub_type_naming_conventions)
  
-   [Conventions de nommage de la propriété déléguée shim ou du champ délégué stub](#BKMK_Shim_delegate_property_or_stub_delegate_field_naming_conventions)
  
-   [Conventions de nommage du type de paramètre](#BKMK_Parameter_type_naming_conventions)
  
-   [Règles récursives](#BKMK_Recursive_rules)  
  
-   [Ressources externes](#BKMK_External_resources)  
  
-   [Aide](#BKMK_Guidance)  
  
##  <a name="BKMK_Code_generation_and_compilation"></a> Génération et compilation de code  
  
###  <a name="BKMK_Configuring_code_generation_of_stubs"></a> Configuration de la génération du code des stubs  
 La génération de types stub est configurée dans un fichier XML avec l’extension de fichier .fakes. Le framework Fakes s'intègre au processus de génération via des tâches personnalisées MSBuild et détecte ces fichiers au moment de la génération. Le générateur de code Fakes compile les types stub dans un assembly et ajoute la référence au projet.  
  
 L'exemple suivant montre des types stub définis dans FileSystem.dll :  
  
```xml  
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">  
    <Assembly Name="FileSystem"/>  
</Fakes>  
  
```  
  
###  <a name="BKMK_Type_filtering"></a> Filtrage de types  
 Les filtres peuvent être définis dans le fichier .fakes pour restreindre les types à extraire. Vous pouvez ajouter un nombre illimité d'éléments Clear, Add, Remove sous l'élément StubGeneration pour générer la liste des types sélectionnés.  
  
 Par exemple, ce fichier .fakes génère des stubs pour les types sous les espaces de noms System et System.IO, mais exclut tout type qui contient « Handle » dans System :  
  
```xml  
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">  
  <Assembly Name="mscorlib" />  
  <!-- user code -->  
  <StubGeneration>  
    <Clear />  
    <Add Namespace="System!" />  
    <Add Namespace="System.IO!"/>  
    <Remove TypeName="Handle" />  
  </StubGeneration>  
  <!-- /user code -->  
</Fakes>  
```  
  
 Les chaînes de filtre utilisent une syntaxe simple pour définir comment la correspondance doit être effectuée :  
  
-   Les filtres ne sont pas sensibles à la casse par défaut ; les filtres effectuent une correspondance de sous-chaîne :  
  
     `el` correspond à « hello »  
  
-   L'ajout de `!` à la fin du filtre en fera une correspondance rigoureusement sensible à la casse :  
  
     `el!` ne correspond pas à « hello »  
  
     `hello!` correspond à « hello »  
  
-   L'ajout de `*` à la fin du filtre le fera correspondre au préfixe de la chaîne :  
  
     `el*` ne correspond pas à « hello »  
  
     `he*` correspond à « hello »  
  
-   Plusieurs filtres dans une liste délimitée par des points-virgules sont combinés comme une disjonction :  
  
     `el;wo` correspond à « hello » et « world »  
  
###  <a name="BKMK_Stubbing_concrete_classes_and_virtual_methods"></a> Classes concrètes et méthodes virtuelles d’opérations stub  
 Par défaut, les types stub sont générés pour toutes les classes non-sealed. Il est possible de restreindre les types stub aux classes abstraites dans le fichier de configuration .fakes :  
  
```xml  
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">  
  <Assembly Name="mscorlib" />  
  <!-- user code -->  
  <StubGeneration>  
    <Types>  
      <Clear />  
      <Add AbstractClasses="true"/>  
    </Types>  
  </StubGeneration>  
  <!-- /user code -->  
</Fakes>  
```  
  
###  <a name="BKMK_Internal_types"></a> Types internes  
 Le générateur de code Fakes génère des types shim et stub pour les types qui sont visibles pour l'assembly généré Fakes. Pour que les types internes d'un assembly ayant fait l'objet d'un shim soient visibles pour l'assembly Fakes et votre assembly de test, ajoutez les attributs <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> au code de l'assembly ayant fait l'objet d'un shim qui donne de la visibilité à l'assembly Fakes généré et à l'assembly de test. Voici un exemple :  
  
```csharp  
// FileSystem\AssemblyInfo.cs  
[assembly: InternalsVisibleTo("FileSystem.Fakes")]  
[assembly: InternalsVisibleTo("FileSystem.Tests")]  
```  
  
 **Types internes dans les assemblys à nom fort**  
  
 Si l'assembly ayant fait l'objet d'un shim porte un nom fort et que vous souhaitez accéder aux types internes de l'assembly :  
  
-   L'assembly de test et l'assembly Fakes doivent porter un nom fort.  
  
-   Vous devez ajouter les clés publiques de l’assembly de test et Fakes aux attributs **InternalsVisibleToAttribute** des assemblys ayant fait l’objet d’un shim. Voici l'apparence des exemples d'attributs dans le code d'assembly ayant fait l'objet d'un shim quand cet assembly porte un nom fort :   
  
    ```csharp  
    // FileSystem\AssemblyInfo.cs  
    [assembly: InternalsVisibleTo("FileSystem.Fakes",  
        PublicKey=<Fakes_assembly_public_key>)]  
    [assembly: InternalsVisibleTo("FileSystem.Tests",  
        PublicKey=<Test_assembly_public_key>)]  
    ```  
  
 Si l'assembly ayant fait l'objet d'un shim porte un nom fort, le framework Fakes signe automatiquement fortement l'assembly Fakes généré. Vous devez signer avec un nom fort l'assembly de test. Consultez [Création et utilisation d’assemblys avec nom fort](http://msdn.microsoft.com/Library/ffbf6d9e-4a88-4a8a-9645-4ce0ee1ee5f9).  
  
 Le framework Fakes utilise la même clé pour signer tous les assemblys générés. Ainsi, vous pouvez utiliser cet extrait de code comme point de départ pour ajouter l’attribut **InternalsVisibleTo** de l’assembly Fakes à votre code assembleur ayant fait l’objet d’un shim.  
  
```csharp  
[assembly: InternalsVisibleTo("FileSystem.Fakes, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e92decb949446f688ab9f6973436c535bf50acd1fd580495aae3f875aa4e4f663ca77908c63b7f0996977cb98fcfdb35e05aa2c842002703cad835473caac5ef14107e3a7fae01120a96558785f48319f66daabc862872b2c53f5ac11fa335c0165e202b4c011334c7bc8f4c4e570cf255190f4e3e2cbc9137ca57cb687947bc")]  
```  
  
 Vous pouvez spécifier une autre clé publique pour l’assembly Fakes, par exemple une clé que vous avez créée pour l’assembly ayant fait l’objet d’un shim, en spécifiant le chemin complet au fichier **.snk** qui contient l’autre clé comme valeur d’attribut `KeyFile` dans l’élément `Fakes`\\`Compilation` du fichier **.fakes**. Exemple :  
  
```xml  
<-- FileSystem.Fakes.fakes -->  
<Fakes ...>  
  <Compilation KeyFile="full_path_to_the_alternate_snk_file" />  
</Fakes>  
  
```  
  
 Vous devez ensuite utiliser la clé publique de l’autre fichier **.snk** comme second paramètre de l’attribut InternalVisibleTo pour l’assembly Fakes dans le code d’assembly ayant fait l’objet d’un shim :  
  
```csharp  
// FileSystem\AssemblyInfo.cs  
[assembly: InternalsVisibleTo("FileSystem.Fakes",  
    PublicKey=<Alternate_public_key>)]  
[assembly: InternalsVisibleTo("FileSystem.Tests",  
    PublicKey=<Test_assembly_public_key>)]  
```  
  
 Dans l'exemple ci-dessus, les valeurs `Alternate_public_key` et `Test_assembly_public_key` peuvent être identiques.  
  
###  <a name="BKMK_Optimizing_build_times"></a> Optimisation de la durée de génération  
 La compilation des assemblys Fakes peut augmenter considérablement la durée de la génération. Vous pouvez réduire la durée de la génération en générant des assemblys Fakes pour les assemblys système .NET et des assemblys tiers dans un projet central séparé. Comme ce genre d'assembly change rarement sur votre ordinateur, vous pouvez réutiliser les assemblys Fakes générés dans d'autres projets.  
  
 Depuis vos projets de test unitaire, vous pouvez simplement prendre une référence aux assemblys Fakes compilés qui sont placés sous FakesAssemblies dans le dossier du projet.  
  
1.  Créez une bibliothèque de classes avec la version du runtime .NET. correspondant à vos projets de test. Appelons-la Fakes.Prebuild. Supprimez le fichier class1.cs du projet, non nécessaire.  
  
2.  Ajoutez la référence à tous les assemblys système et tiers pour lesquels vous avez besoin de Fakes.  
  
3.  Ajoutez un fichier .fakes pour chacun des assemblys et procédez à la génération.  
  
4.  Depuis votre projet de test  
  
    -   Vérifiez que vous avez une référence à la DLL du runtime Fakes :  
  
         C:\Program Files\Microsoft Visual Studio 12.0\Common7\IDE\PublicAssemblies\Microsoft.QualityTools.Testing.Fakes.dll  
  
    -   Pour chaque assembly pour lequel vous avez créé un Fakes, ajoutez une référence au fichier DLL correspondant dans le dossier Fakes.Prebuild\FakesAssemblies de votre projet.  
  
###  <a name="BKMK_Avoiding_assembly_name_clashing"></a> Prévention du conflit de nom d’assembly  
 Dans un environnement Team Build, toutes les sorties de génération sont fusionnées dans un seul répertoire. Dans le cas de plusieurs projets utilisant Fakes, il peut arriver que les assemblys Fakes de versions différentes se substituent. Par exemple, l'assembly Fakes TestProject1 mscorlib.dll de .NET Framework 2.0 et l'assembly Fakes TestProject2 mscorlib.dll de .NET Framework 4 produisent tous deux un assembly Fakes mscorlib.Fakes.dll.  
  
 Pour éviter ce problème, Fakes doit créer automatiquement des noms d'assembly Fakes qualifiés par version pour les références hors projet lors de l'ajout de fichiers .fakes. Un nom d'assembly Fakes qualifié par version inclut un numéro de version quand vous créez le nom d'assembly Fakes :  
  
 Étant donné un assembly MyAssembly et une version 1.2.3.4, le nom de l'assembly Fakes est MyAssembly.1.2.3.4.Fakes.  
  
 Vous pouvez modifier ou supprimer cette version par la modification de l'attribut Version de l'élément Assembly dans le fichier .fakes :   
  
```xml  
attribute of the Assembly element in the .fakes:  
<Fakes ...>  
  <Assembly Name="MyAssembly" Version="1.2.3.4" />  
  ...  
</Fakes>  
  
```  
  
##  <a name="BKMK_Fakes_naming_conventions"></a> Conventions d’affectation de noms Fakes  
  
###  <a name="BKMK_Shim_type_and_stub_type_naming_conventions"></a> Conventions de nommage du type shim et du type stub  
 **Espaces de noms**  
  
-   Le suffixe .Fakes est ajouté à l'espace de noms.  
  
     Par exemple, l'espace de noms `System.Fakes` contient les types shim de l'espace de noms System.  
  
-   Global.Fakes contient le type shim de l'espace de noms vide.  
  
 **Noms de types**  
  
-   Le préfixe shim est ajouté au nom de type pour générer le nom de type shim.  
  
     Par exemple, ShimExample est le type shim du type Example.  
  
-   Le préfixe stub est ajouté au nom de type pour générer le nom de type stub.  
  
     Par exemple, StubIExample est le type stub du type IExample.  
  
 **Arguments de type et structures de type imbriquées**  
  
-   Les arguments de type générique sont copiés.  
  
-   La structure de type imbriquée est copiée pour les types shim.  
  
###  <a name="BKMK_Shim_delegate_property_or_stub_delegate_field_naming_conventions"></a> Conventions de nommage de la propriété déléguée shim ou du champ délégué stub  
 **Règles de base** pour nommer des champs, à partir d’un nom vide :  
  
-   Le nom de la méthode est ajouté.  
  
-   Si le nom de la méthode est une implémentation d'interface explicite, les points sont supprimés.  
  
-   Si la méthode est générique, `Of`*n* est ajouté, où *n* est le nombre d’arguments de méthode générique.  
  
 Les **noms des méthodes spéciales** telles que les accesseurs Get ou Set des propriétés sont traités comme décrit dans le tableau suivant.  
  
|Si la méthode est...|Exemple|Nom de la méthode ajoutée|  
|-------------------|-------------|--------------------------|  
|Un **constructeur**|`.ctor`|`Constructor`|  
|Un **constructeur** statique|`.cctor`|`StaticConstructor`|  
|Un **accesseur** avec le nom de la méthode composé de deux parties séparées par « _ » (tels que les accesseurs Get de propriété)|*nom_genre* (cas général, mais non appliqué par ECMA)|*GenreNom*, où les deux parties ont été mises en majuscules et échangées|  
||Accesseur Get de propriété `Prop`|`PropGet`|  
||Accesseur Set de propriété `Prop`|`PropSet`|  
||Additionneur d'événements|`Add`|  
||Outil de suppression d'événements|`Remove`|  
|Un **opérateur** composé de deux parties|`op_name`|`NameOp`|  
|Par exemple : opérateur + |`op_Add`|`AddOp`|  
|Pour un **opérateur de conversion**, le type de retour est ajouté.|`T op_Implicit`|`ImplicitOpT`|  
  
 **Notes**  
  
-   Les **accesseurs Get et Set des indexeurs** sont traités de la même façon que la propriété. Le nom par défaut pour un indexeur est `Item`.  
  
-   Les noms de **type de paramètre** sont transformés et concaténés.  
  
-   Le **type de retour** est ignoré sauf s’il y a une ambiguïté de surcharge. Si tel est le cas, le type de retour est ajouté à la fin du nom  
  
###  <a name="BKMK_Parameter_type_naming_conventions"></a> Conventions d’affectation de nom de type de paramètre  
  
|Étant donné|La chaîne ajoutée est...|  
|-----------|-------------------------|  
|Un **type**`T`|T<br /><br /> L’espace de noms, la structure imbriquée et les tics génériques sont supprimés.|  
|Un **paramètre de sortie**`out T`|`TOut`|  
|Un **paramètre de référence** `ref T`|`TRef`|  
|Un **type tableau**`T[]`|`TArray`|  
|Un type **tableau multidimensionnel** `T[ , , ]`|`T3`|  
|Un type **pointeur** `T*`|`TPtr`|  
|Un **type générique**`T<R1, ...>`|`TOfR1`|  
|Un **argument de type générique**`!i` de type `C<TType>`|`Ti`|  
|Un **argument de méthode générique**`!!i` de méthode `M<MMethod>`|`Mi`|  
|Un **type imbriqué**`N.T`|`N` est ajouté, puis `T`|  
  
###  <a name="BKMK_Recursive_rules"></a> Règles récursives  
 Les règles suivantes s'appliquent de manière récursive :  
  
-   Étant donné que Fakes utilise C# pour générer les assemblys Fakes, tout caractère qui produirait un jeton C# non valide est défini en séquence d'échappement « _ » (trait de soulignement).  
  
-   Si un nom résultant est en conflit avec un membre du type déclarant, un modèle de numérotation est utilisé en ajoutant un compteur à deux chiffres commençant à 01.  
  
##  <a name="BKMK_External_resources"></a> Ressources externes  
  
###  <a name="BKMK_Guidance"></a> Conseils  
 [Test de la livraison continue avec Visual Studio 2012 - Chapitre 2 : Tests unitaires : tester l’intérieur](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
## <a name="see-also"></a>Voir aussi  
 [Isolation du code testé avec Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)
