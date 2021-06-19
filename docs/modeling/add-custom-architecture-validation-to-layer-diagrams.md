---
title: Ajouter une validation d’architecture personnalisée aux diagrammes de dépendance
description: Fournit des informations sur l’ajout d’une validation d’architecture personnalisée aux diagrammes de dépendance.
ms.date: 11/04/2016
ms.topic: how-to
titleSuffix: ''
helpviewer_keywords:
- dependency diagrams, adding custom validation
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: cc00f86bafebd14177400ffa0ee596a733e9fb28
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384627"
---
# <a name="add-custom-architecture-validation-to-dependency-diagrams"></a>Ajouter une validation d’architecture personnalisée aux diagrammes de dépendance

Dans Visual Studio, les utilisateurs peuvent valider le code source d’un projet par rapport à un modèle de couche afin de vérifier que le code source est conforme aux dépendances sur un diagramme de dépendance. Il existe un algorithme de validation standard, mais vous pouvez définir vos propres extensions de validation.

Lorsque l’utilisateur sélectionne la commande **valider l’architecture** sur un diagramme de dépendance, la méthode de validation standard est appelée, suivie de toutes les extensions de validation installées.

> [!NOTE]
> Dans un diagramme de dépendance, l’objectif principal de la validation est de comparer le diagramme au code du programme dans d’autres parties de la solution.

Vous pouvez empaqueter votre extension de validation de couche dans une extension d’intégration Visual Studio (VSIX) et la distribuer à d’autres utilisateurs de Visual Studio. Vous pouvez soit placer votre validateur seul dans une extension VSIX, soit le combiner dans la même extension VSIX que d’autres extensions. Vous devez écrire le code du validateur dans son propre projet Visual Studio, et non dans le même projet que d’autres extensions.

> [!WARNING]
> Après avoir créé un projet de validation, copiez l’ [exemple de code](#example) à la fin de cette rubrique, puis adaptez-le à vos besoins.

## <a name="requirements"></a>Spécifications

Consultez [spécifications](../modeling/extend-layer-diagrams.md#requirements).

## <a name="defining-a-layer-validator-in-a-new-vsix"></a>Définition d’un validateur de couche dans une nouvelle extension VSIX

Pour créer un validateur, la méthode la plus rapide consiste à utiliser le modèle de projet. Le code et le manifeste VSIX sont alors placés dans le même projet.

### <a name="to-define-an-extension-by-using-a-project-template"></a>Pour définir une extension à l’aide d’un modèle de projet

1. Créez un projet d' **extension de validation du concepteur de couches** .

    Le modèle crée un projet qui contient un petit exemple.

   > [!WARNING]
   > Pour faire fonctionner le modèle correctement :
   >
   > - Modifiez les appels à `LogValidationError` pour supprimer les arguments facultatifs `errorSourceNodes` et `errorTargetNodes`.
   > - Si vous utilisez des propriétés personnalisées, appliquez la mise à jour mentionnée dans [Ajouter des propriétés personnalisées aux diagrammes de dépendance](../modeling/add-custom-properties-to-layer-diagrams.md).

2. Modifiez le code pour définir votre validation. Pour plus d’informations, consultez [Programmation de la validation](#programming).

3. Pour tester l’extension, consultez [Débogage de la validation de couche](#debugging).

   > [!NOTE]
   > Votre méthode est appelée uniquement dans des circonstances spécifiques et les points d’arrêt ne fonctionnent pas automatiquement. Pour plus d’informations, consultez [Débogage de la validation de couche](#debugging).

::: moniker range="vs-2017"

4. Pour installer l’extension dans l’instance principale de Visual Studio, ou sur un autre ordinateur, recherchez le fichier *. vsix* dans le répertoire *bin* . Copiez-le sur l’ordinateur sur lequel vous souhaitez l’installer, puis double-cliquez dessus. Pour le désinstaller, choisissez **extensions et mises à jour** dans le menu **Outils** .

::: moniker-end

::: moniker range=">=vs-2019"

4. Pour installer l’extension dans l’instance principale de Visual Studio, ou sur un autre ordinateur, recherchez le fichier *. vsix* dans le répertoire *bin* . Copiez-le sur l’ordinateur sur lequel vous souhaitez l’installer, puis double-cliquez dessus. Pour le désinstaller, choisissez **gérer les extensions** dans le menu **Extensions** .

::: moniker-end

## <a name="adding-a-layer-validator-to-a-separate-vsix"></a>Ajout d’un validateur de couche à une extension VSIX séparée

Si vous souhaitez créer une extension VSIX qui contient des validateurs de couche, des commandes et d’autres extensions, nous vous recommandons de créer un projet pour définir l’extension VSIX et des projets séparés pour les gestionnaires.

### <a name="to-add-layer-validation-to-a-separate-vsix"></a>Pour ajouter la validation de couche à une extension VSIX séparée

1. Créez un projet de **Bibliothèque de classes**. Ce projet contiendra la classe de validation de couche.

2. Recherchez ou créez un **projet VSIX** dans votre solution. Un projet VSIX contient un fichier nommé **source.extension.vsixmanifest**.

3. Dans **Explorateur de solutions**, dans le menu contextuel du projet VSIX, choisissez **définir comme projet de démarrage**.

4. Dans **source.extension.vsixmanifest**, sous **Composants**, ajoutez le projet de validation de couche en tant que composant MEF :

    1. Sélectionnez **Nouveau**.

    2. Dans la boîte de dialogue **Ajouter un nouveau composant** , définissez les éléments suivants :

         **Type**  =  **Microsoft. VisualStudio. MEFComponent**

         **Source**  =  **Projet dans la solution actuelle**

         **Projet**  =  *votre projet de validateur*

5. Vous devez également l’ajouter en tant que validation de couche :

    1. Sélectionnez **Nouveau**.

    2. Dans la boîte de dialogue **Ajouter un nouveau composant** , définissez les éléments suivants :

         **Type**  =  **Microsoft. VisualStudio. ArchitectureTools. Layer. Validator**. Cette option ne figure pas dans la liste déroulante. Vous devez l’entrer au clavier.

         **Source**  =  **Projet dans la solution actuelle**

         **Projet**  =  *votre projet de validateur*

6. Revenez au projet de validation de couche et ajoutez les références de projet suivantes :

    |**Informations de référence**|**Ce que cela vous permet de faire**|
    |-|-|
    |Microsoft.VisualStudio.GraphModel.dll|Lire le graphique d’architecture|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema.dll|Lire le code DOM associé aux couches|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|Lire le modèle de couche|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility|Lire et mettre à jour des formes et des diagrammes|
    |System.ComponentModel.Composition|Définir le composant de validation à l’aide de Managed Extensibility Framework (MEF)|
    |Microsoft.VisualStudio.Modeling.Sdk.[version]|Définir des extensions de modélisation|

7. Copiez l’exemple de code à la fin de cette rubrique dans le fichier de classe du projet de bibliothèque de validateurs destiné à contenir le code de votre validation. Pour plus d’informations, consultez [Programmation de la validation](#programming).

8. Pour tester l’extension, consultez [Débogage de la validation de couche](#debugging).

    > [!NOTE]
    > Votre méthode est appelée uniquement dans des circonstances spécifiques et les points d’arrêt ne fonctionnent pas automatiquement. Pour plus d’informations, consultez [Débogage de la validation de couche](#debugging).

9. Pour installer l’extension VSIX dans l’instance principale de Visual Studio, ou sur un autre ordinateur, recherchez le fichier **. vsix** dans le répertoire **bin** du projet VSIX. Copiez-le sur l’ordinateur sur lequel vous souhaitez installer l’extension VSIX. Double-cliquez sur le fichier VSIX dans l’Explorateur Windows.

## <a name="programming-validation"></a><a name="programming"></a> Programmation de la validation

Pour définir une extension de validation de couche, définissez une classe avec les caractéristiques suivantes :

- La forme générale de la déclaration se présente comme suit :

  ```csharp
  using System.ComponentModel.Composition;
  using Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema;
  using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
  using Microsoft.VisualStudio.GraphModel;
  ...
   [Export(typeof(IValidateArchitectureExtension))]
    public partial class Validator1Extension :
                    IValidateArchitectureExtension
    {
      public void ValidateArchitecture(Graph graph)
      {
         GraphSchema schema = graph.DocumentSchema;
        ...
    } }
  ```

- Quand vous découvrez une erreur, vous pouvez la signaler à l’aide de `LogValidationError()`.

  > [!WARNING]
  > N’utilisez pas les paramètres facultatifs de `LogValidationError`.

Quand l’utilisateur appelle la commande de menu **Valider l’architecture** , le système runtime de couche analyse les couches et leurs artefacts pour produire un graphique. Le graphique se compose de quatre parties :

- Modèles de couche de la solution Visual Studio représentés sous forme de nœuds et de liens dans le graphique.

- le code, les éléments de projet et d’autres artefacts définis dans la solution et représentés sous forme de nœuds, ainsi que les liens représentant les dépendances découvertes par le processus d’analyse ;

- les liens des nœuds de couche vers les nœuds d’artefact de code ;

- les nœuds représentant les erreurs découvertes par le validateur.

Une fois le graphique construit, la méthode de validation standard est appelée. Quand cette opération est terminée, toutes les méthodes de validation d’extension installées sont appelées dans un ordre non spécifié. Le graphique est passé à chaque méthode `ValidateArchitecture` qui peut analyser le graphique et signaler toutes les erreurs qu’elle rencontre.

> [!NOTE]
> Ce n’est pas le même que le processus de validation qui peut être utilisé dans les langages spécifiques à un domaine.

Les méthodes de validation ne doivent pas modifier le modèle de couche ni le code en cours de validation.

Le modèle de graphique est défini dans <xref:Microsoft.VisualStudio.GraphModel>. Ses classes principales sont <xref:Microsoft.VisualStudio.GraphModel.GraphNode> et <xref:Microsoft.VisualStudio.GraphModel.GraphLink>.

Chaque nœud et chaque lien sont associés à une ou plusieurs catégories qui spécifient le type d’élément ou de relation qu’il représente. Les nœuds d’un graphique type possèdent les catégories suivantes :

- Dsl.LayerModel

- Dsl.Layer

- Dsl.Reference

- CodeSchema_Type

- CodeSchema_Namespace

- CodeSchema_Type

- CodeSchema_Method

- CodeSchema_Field

- CodeSchema_Property

Les liens des couches vers les éléments dans le code ont la catégorie « Représente ».

## <a name="debugging-validation"></a><a name="debugging"></a> Validation du débogage

Pour déboguer votre extension de validation de couche, appuyez sur Ctrl+F5. Une instance expérimentale de Visual Studio s’ouvre. Dans cette instance, ouvrez ou créez un modèle de couche. Ce modèle doit être associé au code et doit avoir au moins une dépendance.

### <a name="test-with-a-solution-that-contains-dependencies"></a>Tester avec une solution contenant des dépendances

La validation n’est exécutée que si les caractéristiques suivantes sont présentes :

- Il existe au moins un lien de dépendance sur le diagramme de dépendance.

- le modèle contient des couches associées aux éléments de code.

La première fois que vous démarrez une instance expérimentale de Visual Studio pour tester votre extension de validation, ouvrez ou créez une solution présentant ces caractéristiques.

### <a name="run-clean-solution-before-validate-architecture"></a>Exécuter la commande Nettoyer la solution avant de valider l’architecture

Chaque fois que vous mettez à jour votre code de validation, utilisez la commande **Nettoyer la solution** du menu **Générer** de la solution expérimentale, et ce avant de tester la commande Valider. Cette opération est nécessaire, car les résultats de la validation sont mis en cache. Si vous n’avez pas mis à jour le diagramme de dépendance de test ou son code, les méthodes de validation ne sont pas exécutées.

### <a name="launch-the-debugger-explicitly"></a>Lancer le débogueur explicitement

La validation s’exécute dans un processus séparé. Par conséquent, les points d’arrêt dans votre méthode de validation ne sont pas déclenchés. Vous devez attacher explicitement le débogueur au processus après le démarrage de la validation.

Pour attacher le débogueur au processus de validation, insérez un appel à `System.Diagnostics.Debugger.Launch()` au début de votre méthode de validation. Quand la boîte de dialogue débogage s’affiche, sélectionnez l’instance principale de Visual Studio.

Vous pouvez également insérer un appel à `System.Windows.Forms.MessageBox.Show()`. Quand la boîte de message s’affiche, accédez à l’instance principale de Visual Studio et, dans le menu **Déboguer** , cliquez sur **attacher au processus**. Sélectionnez le processus nommé **Graphcmd.exe**.

Démarrez toujours l’instance expérimentale en appuyant sur Ctrl+F5 (**Exécuter sans débogage**).

### <a name="deploying-a-validation-extension"></a>Déploiement d’une extension de validation

Pour installer votre extension de validation sur un ordinateur sur lequel une version appropriée de Visual Studio est installée, ouvrez le fichier VSIX sur l’ordinateur cible.

## <a name="example-code"></a><a name="example"></a> Exemple de code

```csharp
using System;
using System.ComponentModel.Composition;
using System.Globalization;
using System.Linq;
using System.Text.RegularExpressions;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
using Microsoft.VisualStudio.GraphModel;

namespace Validator3
{
    [Export(typeof(IValidateArchitectureExtension))]
    public partial class Validator3Extension : IValidateArchitectureExtension
    {
        /// <summary>
        /// Validate the architecture
        /// </summary>
        /// <param name="graph">The graph</param>
        public void ValidateArchitecture(Graph graph)
        {
            if (graph == null) throw new ArgumentNullException("graph");

            // Uncomment the line below to debug this extension during validation
            // System.Windows.Forms.MessageBox.Show("Attach 2 to GraphCmd.exe with process id " + System.Diagnostics.Process.GetCurrentProcess().Id);

            // Get all layers on the diagram
            foreach (GraphNode layer in graph.Nodes.GetByCategory("Dsl.Layer"))
            {
                System.Threading.Thread.Sleep(100);
                // Get the required regex property from the layer node
                string regexPattern = "^[a-zA-Z]+$"; //layer[customPropertyCategory] as string;
                if (!string.IsNullOrEmpty(regexPattern))
                {
                    Regex regEx = new Regex(regexPattern);

                    // Get all referenced types in this layer including those from nested layers so each
                    // type is validated against all containing layer constraints.
                    foreach (GraphNode containedType in layer.FindDescendants().Where(node => node.HasCategory("CodeSchema_Type")))
                    {
                        // Check the type name against the required regex
                        CodeGraphNodeIdBuilder builder = new CodeGraphNodeIdBuilder(containedType.Id, graph);
                        string typeName = builder.Type.Name;
                        if (!regEx.IsMatch(typeName))
                        {
                            // Log an error
                            string message = string.Format(CultureInfo.CurrentCulture, Resources.InvalidTypeNameMessage, typeName);
                            this.LogValidationError(graph, typeName + "TypeNameError", message, GraphErrorLevel.Error, layer);
                        }
                    }
                }

            }

        }
    }
}
```

## <a name="see-also"></a>Voir aussi

- [Étendre des diagrammes de dépendance](../modeling/extend-layer-diagrams.md)
