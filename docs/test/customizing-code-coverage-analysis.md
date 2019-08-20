---
title: Personnalisation de l'analyse de couverture du code
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 8749cd7757796a1b716b1ac9db086d3155f94694
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62965547"
---
# <a name="customize-code-coverage-analysis"></a>Personnaliser l’analyse de la couverture du code

Par défaut, la couverture du code analyse tous les assemblys de la solution chargés pendant les tests unitaires. Nous vous recommandons d’utiliser ce comportement par défaut, car il est généralement efficace. Pour plus d’informations, consultez [Utiliser la couverture du code pour déterminer la quantité de code testé](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

Pour exclure le code de test des résultats de la couverture du code et inclure uniquement le code d’application, ajoutez l’attribut <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> à votre classe de test.

Pour inclure des assemblys qui ne font pas partie de votre solution, obtenez les fichiers *.pdb* de ces assemblys et copiez-les dans le même dossier que les fichiers *.dll* de l’assembly.

## <a name="run-settings-file"></a>Fichier de paramètres d’exécution

Le [fichier de paramètres d’exécution](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md) est le fichier de configuration utilisé par les outils de test unitaire. Les paramètres avancés de la couverture du code sont spécifiées dans un fichier *.runsettings*.

Pour personnaliser la couverture du code, effectuez les étapes suivantes :

1. Ajoutez un fichier de paramètres d’exécution à votre solution. Dans **l’Explorateur de solutions**, dans le menu contextuel de votre solution, choisissez **Ajouter** > **Nouvel élément**, puis sélectionnez **Fichier XML**. Enregistrez le fichier sous un nom comme *CodeCoverage.runsettings*.

1. Ajoutez le contenu de l’exemple de fichier à la fin de cet article, puis personnalisez-le selon vos besoins comme décrit dans les sections qui suivent.

1. Pour sélectionner le fichier de paramètres d’exécution, dans le menu **Test**, choisissez **Paramètres de test** > **Sélectionner le fichier de paramètres des tests**. Pour spécifier un fichier de paramètres d’exécution afin d’exécuter des tests depuis la ligne de commande ou dans un flux de travail de build, consultez [Configurer des tests unitaires à l’aide d’un fichier *.runsettings*](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md#specify-a-run-settings-file).

   Quand vous sélectionnez **Analyser la couverture du code**, les informations de configuration sont lues à partir du fichier de paramètres d’exécution.

   > [!TIP]
   > Les résultats de la couverture du code et la coloration du code précédents ne sont pas automatiquement masqués quand vous exécutez des tests ou que vous mettez à jour votre code.

Pour activer ou désactiver les paramètres personnalisés, désélectionnez ou sélectionnez le fichier dans le menu **Test** > **Paramètres de test**.

![Menu Paramètres de test avec le fichier de paramètres de test](../test/media/codecoverage-settingsfile.png)

### <a name="specify-symbol-search-paths"></a>Spécifier les chemins de recherche de symboles

La couverture du code requiert des fichiers de symboles (fichiers *.pdb*) pour les assemblys. Pour les assemblys générés par votre solution, les fichiers de symboles sont généralement présents à côté des fichiers binaires, et la couverture du code s’exécute automatiquement. Mais, dans certains cas, vous pouvez inclure les assemblys référencés dans votre analyse de couverture du code. Dans ce cas, les fichiers *.pdb* peuvent ne pas être adjacents aux fichiers binaires, mais vous pouvez spécifier le chemin de recherche de symboles dans le fichier *.runsettings*.

```xml
<SymbolSearchPaths>
      <Path>\\mybuildshare\builds\ProjectX</Path>
      <!--More paths if required-->
</SymbolSearchPaths>
```

> [!NOTE]
> La résolution des symboles peut prendre du temps, surtout quand vous utilisez un emplacement de fichier distant avec de nombreux assemblys. Ainsi, envisagez de copier les fichiers *.pdb* au même emplacement local que les fichiers binaires ( *.dll* et *.exe*).

### <a name="exclude-and-include"></a>Exclure et inclure

Vous pouvez exclure les assemblys spécifiés de l'analyse de couverture du code. Par exemple :

```xml
<ModulePaths>
  <Exclude>
   <ModulePath>Fabrikam.Math.UnitTest.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Exclude>
</ModulePaths>
```

Sinon, vous pouvez spécifier les assemblys doivent être inclus. Cette approche présente l'inconvénient suivant : lorsque vous ajoutez des assemblys à la solution, vous devez penser à les ajouter à la liste :

```xml
<ModulePaths>
  <Include>
   <ModulePath>Fabrikam.Math.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Include>
</ModulePaths>
```

Si **Include** est vide, le traitement de la couverture du code inclut tous les assemblys qui sont chargés et pour lesquels les fichiers *.pdb* sont trouvés. La couverture du code n’inclut pas les éléments qui correspondent à une clause dans une liste **Exclude**.

**Include** est traité avant **Exclude**.

### <a name="regular-expressions"></a>Expressions régulières

Les nœuds inclure et exclure utilisent des expressions régulières. Pour plus d’informations, consultez [Utiliser des expressions régulières dans Visual Studio](../ide/using-regular-expressions-in-visual-studio.md). Les expressions régulières ne sont pas l’équivalent des caractères génériques. En particulier :

- **.\\** * correspond à une chaîne de caractères (quels qu’ils soient)

- **\\.** correspond à un point « . »

- **\\(   \\)** correspond à des parenthèses « (  ) »

- **\\\\** correspond à un séparateur de chemin de fichier « \\ »

- **^** correspond au début de la chaîne

- **$** correspond la fin de la chaîne

Les correspondances ne respectent pas la casse.

Par exemple :

```xml
<ModulePaths>
  <Include>
    <!-- Include all loaded .dll assemblies (but not .exe assemblies): -->
    <ModulePath>.*\.dll$</ModulePath>
  </Include>
  <Exclude>
    <!-- But exclude some assemblies: -->
    <ModulePath>.*\\Fabrikam\.MyTests1\.dll$</ModulePath>
    <!-- Exclude all file paths that contain "Temp": -->
    <ModulePath>.*Temp.*</ModulePath>
  </Exclude>
</ModulePaths>
```

> [!WARNING]
> S’il existe une erreur dans une expression régulière, telle qu’une séquence d’échappement ou une parenthèse sans correspondance, l’analyse de couverture du code ne fonctionne pas.

### <a name="other-ways-to-include-or-exclude-elements"></a>Autres façons d'inclure ou d'exclure des éléments

- **ModulePath** : correspond aux assemblys spécifiés par le chemin de fichier d’assembly.

- **CompanyName** : correspond aux assemblys par l’attribut **Société**.

- **PublicKeyToken** : correspond aux assemblys signés par le jeton de clé publique.

- **Source** : correspond à des éléments par le chemin du fichier source dans lequel ils sont définis.

- **Attribute** : correspond à des éléments auxquels un attribut spécial est attaché. Spécifiez le nom complet de l’attribut et insérez « Attribute » à la fin du nom.

- **Function** : correspond à des procédures, des fonctions ou des méthodes par le nom qualifié complet. Pour correspondre à un nom de fonction, l’expression régulière doit correspondre au nom complet de la fonction, y compris l’espace de noms, le nom de classe, le nom de méthode et la liste des paramètres. Par exemple :

   ```csharp
   Fabrikam.Math.LocalMath.SquareRoot(double);
   ```

   ```cpp
   Fabrikam::Math::LocalMath::SquareRoot(double)
   ```

   ```xml
   <Functions>
     <Include>
       <!-- Include methods in the Fabrikam namespace: -->
       <Function>^Fabrikam\..*</Function>
       <!-- Include all methods named EqualTo: -->
       <Function>.*\.EqualTo\(.*</Function>
     </Include>
     <Exclude>
       <!-- Exclude methods in a class or namespace named UnitTest: -->
       <Function>.*\.UnitTest\..*</Function>
     </Exclude>
   </Functions>
   ```

## <a name="sample-runsettings-file"></a>Fichier d'exemple .runsettings

Copiez ce code et modifiez-le selon vos besoins.

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- File name extension must be .runsettings -->
<RunSettings>
  <DataCollectionRunSettings>
    <DataCollectors>
      <DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
        <Configuration>
          <CodeCoverage>
<!--
Additional paths to search for .pdb (symbol) files. Symbols must be found for modules to be instrumented.
If .pdb files are in the same folder as the .dll or .exe files, they are automatically found. Otherwise, specify them here.
Note that searching for symbols increases code coverage runtime. So keep this small and local.
-->
<!--
            <SymbolSearchPaths>
                   <Path>C:\Users\User\Documents\Visual Studio 2012\Projects\ProjectX\bin\Debug</Path>
                   <Path>\\mybuildshare\builds\ProjectX</Path>
            </SymbolSearchPaths>
-->

<!--
About include/exclude lists:
Empty "Include" clauses imply all; empty "Exclude" clauses imply none.
Each element in the list is a regular expression (ECMAScript syntax). See https://docs.microsoft.com/visualstudio/ide/using-regular-expressions-in-visual-studio.
An item must first match at least one entry in the include list to be included.
Included items must then not match any entries in the exclude list to remain included.
-->

            <!-- Match assembly file paths: -->
            <ModulePaths>
              <Include>
                <ModulePath>.*\.dll$</ModulePath>
                <ModulePath>.*\.exe$</ModulePath>
              </Include>
              <Exclude>
                <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
              </Exclude>
            </ModulePaths>

            <!-- Match fully qualified names of functions: -->
            <!-- (Use "\." to delimit namespaces in C# or Visual Basic, "::" in C++.)  -->
            <Functions>
              <Exclude>
                <Function>^Fabrikam\.UnitTest\..*</Function>
                <Function>^std::.*</Function>
                <Function>^ATL::.*</Function>
                <Function>.*::__GetTestMethodInfo.*</Function>
                <Function>^Microsoft::VisualStudio::CppCodeCoverageFramework::.*</Function>
                <Function>^Microsoft::VisualStudio::CppUnitTestFramework::.*</Function>
              </Exclude>
            </Functions>

            <!-- Match attributes on any code element: -->
            <Attributes>
              <Exclude>
                <!-- Don't forget "Attribute" at the end of the name -->
                <Attribute>^System\.Diagnostics\.DebuggerHiddenAttribute$</Attribute>
                <Attribute>^System\.Diagnostics\.DebuggerNonUserCodeAttribute$</Attribute>
                <Attribute>^System\.Runtime\.CompilerServices.CompilerGeneratedAttribute$</Attribute>
                <Attribute>^System\.CodeDom\.Compiler.GeneratedCodeAttribute$</Attribute>
                <Attribute>^System\.Diagnostics\.CodeAnalysis.ExcludeFromCodeCoverageAttribute$</Attribute>
              </Exclude>
            </Attributes>

            <!-- Match the path of the source files in which each method is defined: -->
            <Sources>
              <Exclude>
                <Source>.*\\atlmfc\\.*</Source>
                <Source>.*\\vctools\\.*</Source>
                <Source>.*\\public\\sdk\\.*</Source>
                <Source>.*\\microsoft sdks\\.*</Source>
                <Source>.*\\vc\\include\\.*</Source>
              </Exclude>
            </Sources>

            <!-- Match the company name property in the assembly: -->
            <CompanyNames>
              <Exclude>
                <CompanyName>.*microsoft.*</CompanyName>
              </Exclude>
            </CompanyNames>

            <!-- Match the public key token of a signed assembly: -->
            <PublicKeyTokens>
              <!-- Exclude Visual Studio extensions: -->
              <Exclude>
                <PublicKeyToken>^B77A5C561934E089$</PublicKeyToken>
                <PublicKeyToken>^B03F5F7F11D50A3A$</PublicKeyToken>
                <PublicKeyToken>^31BF3856AD364E35$</PublicKeyToken>
                <PublicKeyToken>^89845DCD8080CC91$</PublicKeyToken>
                <PublicKeyToken>^71E9BCE111E9429C$</PublicKeyToken>
                <PublicKeyToken>^8F50407C4E9E73B6$</PublicKeyToken>
                <PublicKeyToken>^E361AF139669C375$</PublicKeyToken>
              </Exclude>
            </PublicKeyTokens>

            <!-- We recommend you do not change the following values: -->
            <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
            <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
            <CollectFromChildProcesses>True</CollectFromChildProcesses>
            <CollectAspDotNet>False</CollectAspDotNet>

          </CodeCoverage>
        </Configuration>
      </DataCollector>
    </DataCollectors>
  </DataCollectionRunSettings>
</RunSettings>
```

## <a name="see-also"></a>Voir aussi

- [Configurer des tests unitaires à l’aide d’un fichier .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [Utiliser la couverture du code pour déterminer la quantité de code testé](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
- [Tests unitaires sur votre code](../test/unit-test-your-code.md)