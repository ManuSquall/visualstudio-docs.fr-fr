---
title: Connecter l’hôte au processeur de directive généré
description: Découvrez comment vous pouvez développer votre hôte personnalisé pour qu’il prenne en charge les modèles de texte qui appellent des processeurs de directive.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- walkthroughs [text templates], connecting host to processor
- text templates, custom directive hosts
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
dev_langs:
- CSharp
- VB
ms.openlocfilehash: ed51688e5b65e34d7067963dbf7b839b1f022768
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388319"
---
# <a name="walkthrough-connect-a-host-to-a-generated-directive-processor"></a>Procédure pas à pas : connecter un hôte à un processeur de directive généré

Vous pouvez écrire votre propre hôte qui traite les modèles de texte. Un hôte personnalisé de base est illustré dans [procédure pas à pas : création d’un hôte de modèle de texte personnalisé](../modeling/walkthrough-creating-a-custom-text-template-host.md). Vous pouvez étendre cet hôte pour ajouter des fonctions telles que la génération de plusieurs fichiers de sortie.

Dans cette procédure pas à pas, vous développez votre hôte personnalisé afin qu’il prenne en charge les modèles de texte qui appellent des processeurs de directive. Lorsque vous définissez un langage spécifique à un domaine, il génère un *processeur de directive* pour le modèle de domaine. Le processeur de directive permet aux utilisateurs d’écrire plus facilement des modèles qui accèdent au modèle, ce qui réduit la nécessité d’écrire des directives d’assembly et d’importation dans les modèles.

> [!NOTE]
> Cette procédure pas à pas s’appuie sur la [procédure pas à pas : création d’un hôte de modèle de texte personnalisé](../modeling/walkthrough-creating-a-custom-text-template-host.md). Effectuez d’abord cette procédure pas à pas.

Cette procédure pas à pas comprend les tâches suivantes :

- Utilisation [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] de pour générer un processeur de directive basé sur un modèle de domaine.

- Connexion d’un hôte de modèle de texte personnalisé au processeur de directive généré.

- Test de l’hôte personnalisé avec le processeur de directive généré.

## <a name="prerequisites"></a>Prérequis

Pour définir un DSL, vous devez avoir installé les composants suivants :

| Composant | Lien |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index) |
| Kit de développement logiciel (SDK) Visual Studio Visualization and Modeling | |

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

En outre, vous devez avoir créé la transformation de modèle de texte personnalisée dans [procédure pas à pas : création d’un hôte de modèle de texte personnalisé](../modeling/walkthrough-creating-a-custom-text-template-host.md).

## <a name="use-domain-specific-language-tools-to-generate-a-directive-processor"></a>Utiliser les outils de langage Domain-Specific pour générer un processeur de directive

Dans cette procédure pas à pas, vous utilisez l’Assistant concepteur de langage Domain-Specific pour créer un langage spécifique à un domaine pour la solution DSLMinimalTest.

1. Créez une solution de langage spécifique à un domaine qui présente les caractéristiques suivantes :

   - Nom : DSLMinimalTest

   - Modèle de solution : langage minimal

   - Extension de fichier : min

   - Nom de la société : fabrikam

   Pour plus d’informations sur la création d’une solution de langage spécifique à un domaine, consultez [How to : Create a Domain-Specific Language solution](../modeling/how-to-create-a-domain-specific-language-solution.md).

2. Dans le menu **Générer**, cliquez sur **Générer la solution**.

   > [!IMPORTANT]
   > Cette étape génère le processeur de directive et y ajoute la clé dans le registre.

3. Dans le menu **Déboguer** , cliquez sur **Démarrer le débogage**.

    Une deuxième instance de Visual Studio s’ouvre.

4. Dans la build expérimentale, dans **Explorateur de solutions**, double-cliquez sur le fichier **Sample. min**.

    Le fichier s’ouvre dans le concepteur. Notez que le modèle a deux éléments, ExampleElement1 et ExampleElement2, et un lien entre eux.

5. Fermez la deuxième instance de Visual Studio.

6. Enregistrez la solution, puis fermez le concepteur de langage Domain-Specific.

## <a name="connect-a-custom-text-template-host-to-a-directive-processor"></a>Connecter un hôte de modèle de texte personnalisé à un processeur de directive

Une fois que vous avez généré le processeur de directive, vous connectez le processeur de directive et l’hôte de modèle de texte personnalisé que vous avez créé dans [procédure pas à pas : création d’un hôte de modèle de texte personnalisé](../modeling/walkthrough-creating-a-custom-text-template-host.md).

1. Ouvrez la solution CustomHost.

2. Dans le menu **Projet**, cliquez sur **Ajouter une référence**.

     La boîte de dialogue **Ajouter une référence** s’ouvre et affiche l’onglet **.net** .

3. Ajoutez les références suivantes :

    - Microsoft. VisualStudio. Modeling. Sdk. 11.0

    - Microsoft. VisualStudio. Modeling. Sdk. Diagrams. 11.0

    - Microsoft. VisualStudio. TextTemplating. 11.0

    - Microsoft. VisualStudio. TextTemplating. interfaces. 11.0

    - Microsoft. VisualStudio. TextTemplating. Modeling. 11.0

    - Microsoft. VisualStudio. TextTemplating. VSHost. 11.0

4. En haut de Program. cs ou Module1. vb, ajoutez la ligne de code suivante :

    ```csharp
    using Microsoft.Win32;
    ```

    ```vb
    Imports Microsoft.Win32
    ```

5. Recherchez le code de la propriété `StandardAssemblyReferences` et remplacez-le par le code suivant :

    > [!NOTE]
    > Dans cette étape, vous ajoutez des références aux assemblys qui sont requis par le processeur de directive généré que votre hôte prendra en charge.

    ```csharp
    //the host can provide standard assembly references
    //the engine will use these references when compiling and
    //executing the generated transformation class
    //--------------------------------------------------------------
    public IList<string> StandardAssemblyReferences
    {
        get
        {
            return new string[]
            {
                //if this host searches standard paths and the GAC
                //we can specify the assembly name like this:
                //"System"
                //since this host only resolves assemblies from the
                //fully qualified path and name of the assembly
                //this is a quick way to get the code to give us the
                //fully qualified path and name of the System assembly
                //---------------------------------------------------------
                typeof(System.Uri).Assembly.Location,
                            typeof(System.Uri).Assembly.Location,
                typeof(Microsoft.VisualStudio.Modeling.ModelElement).Assembly.Location,
                typeof(Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape).Assembly.Location,
                typeof(Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating).Assembly.Location,
                typeof(Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation).Assembly.Location

            };
        }
    }
    ```

6. Recherchez le code de la fonction `ResolveDirectiveProcessor` et remplacez-le par le code suivant :

    > [!IMPORTANT]
    > Ce code contient des références codées en dur au nom du processeur de directive généré auquel vous souhaitez vous connecter. Vous pouvez facilement le rendre plus général, auquel cas il recherche tous les processeurs de directive listés dans le registre et tente de trouver une correspondance. Dans ce cas, l’hôte fonctionne avec n’importe quel processeur de directive généré.

    ```csharp
    //the engine calls this method based on the directives the user has
            //specified it in the text template
            //this method can be called 0, 1, or more times
            //---------------------------------------------------------------------
            public Type ResolveDirectiveProcessor(string processorName)
            {
                //check the processor name, and if it is the name of the processor the
                //host wants to support, return the type of the processor
                //---------------------------------------------------------------------
                if (string.Compare(processorName, "DSLMinimalTestDirectiveProcessor", StringComparison.InvariantCultureIgnoreCase) == 0)
                {
                    try
                    {
                        string keyName = @"Software\Microsoft\VisualStudio\10.0Exp_Config\TextTemplating\DirectiveProcessors\DSLMinimalTestDirectiveProcessor";
                        using (RegistryKey specificKey = Registry.CurrentUser.OpenSubKey(keyName))
                        {
                            if (specificKey != null)
                            {
                                List<string> names = new List<String>(specificKey.GetValueNames());
                                string classValue = specificKey.GetValue("Class") as string;
                                if (!string.IsNullOrEmpty(classValue))
                                {
                                    string loadValue = string.Empty;
                                    System.Reflection.Assembly processorAssembly = null;
                                    if (names.Contains("Assembly"))
                                    {
                                        loadValue = specificKey.GetValue("Assembly") as string;
                                        if (!string.IsNullOrEmpty(loadValue))
                                        {
                                            //the assembly must be installed in the GAC
                                            processorAssembly = System.Reflection.Assembly.Load(loadValue);
                                        }
                                    }
                                    else if (names.Contains("CodeBase"))
                                    {
                                        loadValue = specificKey.GetValue("CodeBase") as string;
                                        if (!string.IsNullOrEmpty(loadValue))
                                        {
                                            //loading local assembly
                                            processorAssembly = System.Reflection.Assembly.LoadFrom(loadValue);
                                        }
                                    }
                                    if (processorAssembly == null)
                                    {
                                        throw new Exception("Directive Processor not found");
                                    }
                                    Type processorType = processorAssembly.GetType(classValue);
                                    if (processorType == null)
                                    {
                                        throw new Exception("Directive Processor not found");
                                    }
                                    return processorType;
                                }
                            }
                        }
                    }
                    catch (Exception e)
                    {
                        //if the directive processor can not be found, throw an error
                        throw new Exception("Directive Processor not found");
                    }
                }

                //if the directive processor is not one this host wants to support
                throw new Exception("Directive Processor not supported");
            }
    ```

7. Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.

8. Dans le menu **Générer**, cliquez sur **Générer la solution**.

## <a name="test-the-custom-host-with-the-directive-processor"></a>Test de l’hôte personnalisé avec le processeur de directive

Pour tester l’hôte de modèle de texte personnalisé, vous devez d’abord écrire un modèle de texte qui appelle le processeur de directive généré. Ensuite, vous exécutez l’hôte personnalisé, vous lui transmettez le nom du modèle de texte et vous vérifiez que la directive est traitée correctement.

### <a name="create-a-text-template-to-test-the-custom-host"></a>Créer un modèle de texte pour tester l’hôte personnalisé

1. Créez un fichier texte et nommez-le `TestTemplateWithDP.tt` . Vous pouvez utiliser n’importe quel éditeur de texte, tel que le bloc-notes, pour créer le fichier.

2. Ajoutez le code suivant au fichier texte :

    > [!NOTE]
    > Le langage de programmation du modèle de texte ne doit pas nécessairement correspondre à celui de l’hôte personnalisé.

    ```csharp
    Text Template Host Test

    <#@ template debug="true" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>
    <# //this is the call to the examplemodel directive in the generated directive processor #>
    <#@ DSLMinimalTest processor="DSLMinimalTestDirectiveProcessor" requires="fileName='<Your Path>\Sample.min'" provides="ExampleModel=ExampleModel" #>
    <# //uncomment this line to test that the host allows the engine to set the extension #>
    <# //@ output extension=".htm" #>

    <# //uncomment this line if you want to see the generated transformation class #>
    <# //System.Diagnostics.Debugger.Break(); #>
    <# //this code uses the results of the examplemodel directive #>
    <#
        foreach ( ExampleElement box in this.ExampleModel.Elements )
        {
            WriteLine("Box: {0}", box.Name);

            foreach (ExampleElement linkedTo in box.Targets)
            {
                WriteLine("Linked to: {0}", linkedTo.Name);
            }

            foreach (ExampleElement linkedFrom in box.Sources)
            {
                WriteLine("Linked from: {0}", linkedFrom.Name);
            }

            WriteLine("");
        }
    #>
    ```

    ```vb
    Text Template Host Test

    <#@ template debug="true" language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>

    <# 'this is the call to the examplemodel directive in the generated directive processor #>
    <#@ DSLMinimalTest processor="DSLMinimalTestDirectiveProcessor" requires="fileName='<Your Path>\Sample.min'" provides="ExampleModel=ExampleModel" #>

    <# 'Uncomment this line to test that the host allows the engine to set the extension. #>
    <# '@ output extension=".htm" #>

    <# 'Uncomment this line if you want to see the generated transformation class. #>
    <# 'System.Diagnostics.Debugger.Break() #>

    <# 'this code uses the results of the examplemodel directive #>

    <#
       For Each box as ExampleElement In Me.ExampleModel.Elements

           WriteLine("Box: {0}", box.Name)

            For Each LinkedTo as ExampleElement In box.Targets
                WriteLine("Linked to: {0}", LinkedTo.Name)
            Next

            For Each LinkedFrom as ExampleElement In box.Sources
                WriteLine("Linked from: {0}", LinkedFrom.Name)
            Next

            WriteLine("")

       Next
    #>
    ```

3. Dans le code, remplacez \<YOUR PATH> par le chemin d’accès du fichier Sample. min à partir du langage spécifique à la conception que vous avez créé dans la première procédure.

4. Enregistrez et fermez le fichier.

### <a name="test-the-custom-host"></a>Tester l’hôte personnalisé

1. Ouvrez une fenêtre d’invite de commandes.

2. Tapez le chemin d’accès du fichier exécutable de l’hôte personnalisé, mais n’appuyez pas encore sur ENTRÉE.

     Par exemple, entrez :

     `<YOUR PATH>CustomHost\bin\Debug\CustomHost.exe`

    > [!NOTE]
    > Au lieu de taper l’adresse, vous pouvez accéder au fichier CustomHost.exe dans l' **Explorateur Windows**, puis faire glisser le fichier dans la fenêtre d’invite de commandes.

3. Tapez un espace.

4. Tapez le chemin d'accès du fichier modèle de texte, puis appuyez sur ENTRÉE.

     Par exemple, entrez :

     `<YOUR PATH>TestTemplateWithDP.txt`

    > [!NOTE]
    > Au lieu de taper l’adresse, vous pouvez accéder au fichier TestTemplateWithDP.txt dans l' **Explorateur Windows**, puis faire glisser le fichier dans la fenêtre d’invite de commandes.

     L’application hôte personnalisée s’exécute et démarre le processus de transformation du modèle de texte.

5. Dans l' **Explorateur Windows**, accédez au dossier qui contient le fichier TestTemplateWithDP.txt.

     Le dossier contient également le fichier TestTemplateWithDP1.txt.

6. Ouvrez ce fichier pour afficher les résultats de la transformation du modèle de texte.

     Les résultats de la sortie de texte générée apparaissent et doivent ressembler à ceci :

    ```
    Text Template Host Test

    Box: ExampleElement1
    Linked to: ExampleElement2

    Box: ExampleElement2
    Linked from: ExampleElement1
    ```

## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : création d'un hôte de modèle de texte personnalisé](../modeling/walkthrough-creating-a-custom-text-template-host.md)
