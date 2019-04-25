---
title: Ajouter une validation d’architecture personnalisée aux diagrammes de couche | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, adding custom validation
ms.assetid: fed7bc08-295a-46d6-9fd8-fb537f1f75f1
caps.latest.revision: 44
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b91f89bc6c3db52526c8c5e64549b08310a17313
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60045877"
---
# <a name="add-custom-architecture-validation-to-layer-diagrams"></a>Ajouter une validation d'architecture personnalisée aux diagrammes de couche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans Visual Studio, les utilisateurs peuvent valider le code source dans un projet par rapport à un modèle de couche de manière à vérifier que le code source est conforme aux dépendances sur un diagramme de couche. Il existe un algorithme de validation standard, mais vous pouvez définir vos propres extensions de validation.  
  
 Quand l’utilisateur sélectionne la commande **Valider l’architecture** sur un diagramme de couche, la méthode de validation standard est appelée, suivie de toutes les extensions de validation installées.  
  
> [!NOTE]
>  La validation dans un diagramme de couche est différente de la validation dans les diagrammes UML. Dans un diagramme de couche, le but principal est de comparer le diagramme au code du programme dans d’autres parties de la solution.  
  
 Vous pouvez empaqueter votre extension de validation de couche dans une extension d’intégration Visual Studio (VSIX) et la distribuer à d’autres utilisateurs de Visual Studio. Vous pouvez soit placer votre validateur seul dans une extension VSIX, soit le combiner dans la même extension VSIX que d’autres extensions. Vous devez écrire le code du validateur dans son propre projet Visual Studio, et non dans le même projet que d’autres extensions.  
  
> [!WARNING]
>  Après avoir créé un projet de validation, copiez l’ [exemple de code](#example) à la fin de cette rubrique, puis adaptez-le à vos besoins.  
  
## <a name="requirements"></a>Configuration requise  
 Consultez [Spécifications](../modeling/extend-layer-diagrams.md#prereqs).  
  
## <a name="defining-a-layer-validator-in-a-new-vsix"></a>Définition d’un validateur de couche dans une nouvelle extension VSIX  
 Pour créer un validateur, la méthode la plus rapide consiste à utiliser le modèle de projet. Le code et le manifeste VSIX sont alors placés dans le même projet.  
  
#### <a name="to-define-an-extension-by-using-a-project-template"></a>Pour définir une extension à l’aide d’un modèle de projet  
  
1. Créez un projet dans une nouvelle solution en sélectionnant la commande **Nouveau projet** dans le menu **Fichier** .  
  
2. Dans la boîte de dialogue **Nouveau projet** , sous **Projets de modélisation**, cliquez sur **Layer Designer Validation Extension**(Extension de validation du concepteur de couche).  
  
    Le modèle crée un projet qui contient un petit exemple.  
  
   > [!WARNING]
   >  Makethe modèle fonctionne correctement :  
   > 
   > - Modifiez les appels à `LogValidationError` pour supprimer les arguments facultatifs `errorSourceNodes` et `errorTargetNodes`.  
   >   - Si vous utilisez des propriétés personnalisées, appliquez la mise à jour mentionnée dans [ajouter des propriétés personnalisées aux diagrammes de couche](../modeling/add-custom-properties-to-layer-diagrams.md).  
  
3. Modifiez le code pour définir votre validation. Pour plus d’informations, consultez [Programmation de la validation](#programming).  
  
4. Pour tester l’extension, consultez [Débogage de la validation de couche](#debugging).  
  
   > [!NOTE]
   >  Votre méthode est appelée uniquement dans des circonstances spécifiques et les points d’arrêt ne fonctionnent pas automatiquement. Pour plus d’informations, consultez [Débogage de la validation de couche](#debugging).  
  
5. Pour installer l’extension dans l’instance principale de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ou sur un autre ordinateur, recherchez le fichier **.vsix** dans *bin\\*. Copiez-le sur l’ordinateur sur lequel vous souhaitez l’installer, puis double-cliquez dessus. Pour le désinstaller, utilisez **Extensions et mises à jour** dans le menu **Outils** .  
  
## <a name="adding-a-layer-validator-to-a-separate-vsix"></a>Ajout d’un validateur de couche à une extension VSIX séparée  
 Si vous souhaitez créer une extension VSIX qui contient des validateurs de couche, des commandes et d’autres extensions, nous vous recommandons de créer un projet pour définir l’extension VSIX et des projets séparés pour les gestionnaires. Pour plus d’informations sur les autres types d’extensions de modélisation, consultez [modèles et diagrammes UML étendre](../modeling/extend-uml-models-and-diagrams.md).  
  
#### <a name="to-add-layer-validation-to-a-separate-vsix"></a>Pour ajouter la validation de couche à une extension VSIX séparée  
  
1. Créez un projet de bibliothèque de classes dans une solution Visual Studio nouvelle ou existante. Dans la boîte de dialogue **Nouveau projet** , cliquez sur **Visual C#** , puis sur **Bibliothèque de classes**. Ce projet contiendra la classe de validation de couche.  
  
2. Identifiez ou créez un projet VSIX dans votre solution. Un projet VSIX contient un fichier nommé **source.extension.vsixmanifest**. Si vous devez ajouter un projet VSIX, procédez comme suit :  
  
    1. Dans la boîte de dialogue **Nouveau projet** , choisissez **Visual C#**, **Extensibilité**, **Projet VSIX**.  
  
    2. Dans l’ **Explorateur de solutions**, dans le menu contextuel du projet VSIX, choisissez **Définir comme projet de démarrage**.  
  
3. Dans **source.extension.vsixmanifest**, sous **Composants**, ajoutez le projet de validation de couche en tant que composant MEF :  
  
    1. Choisissez **Nouveau**.  
  
    2. Dans la boîte de dialogue **Ajouter un nouveau composant** , définissez les éléments suivants :  
  
         **Type** = **Microsoft.VisualStudio.MefComponent**  
  
         **Source** = **Projet dans la solution actuelle**  
  
         **Projet** = *votre projet de validateur*  
  
4. Vous devez également l’ajouter en tant que validation de couche :  
  
    1. Choisissez **Nouveau**.  
  
    2. Dans la boîte de dialogue **Ajouter un nouveau composant** , définissez les éléments suivants :  
  
         **Type** = **Microsoft.VisualStudio.ArchitectureTools.Layer.Validator**. Cette option ne figure pas dans la liste déroulante. Vous devez l’entrer au clavier.  
  
         **Source** = **Projet dans la solution actuelle**  
  
         **Projet** = *votre projet de validateur*  
  
5. Revenez au projet de validation de couche et ajoutez les références de projet suivantes :  
  
    |**Référence**|**Ce que cela vous permet de faire**|  
    |-------------------|------------------------------------|  
    |Microsoft.VisualStudio.GraphModel.dll|Lire le graphique d’architecture|  
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema.dll|Lire le code DOM associé aux couches|  
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|Lire le modèle de couche|  
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility|Lire et mettre à jour des formes et des diagrammes|  
    |System.ComponentModel.Composition|Définir le composant de validation à l’aide de Managed Extensibility Framework (MEF)|  
    |Microsoft.VisualStudio.Modeling.Sdk.[version]|Définir des extensions de modélisation|  
  
6. Copiez l’exemple de code à la fin de cette rubrique dans le fichier de classe du projet de bibliothèque de validateurs destiné à contenir le code de votre validation. Pour plus d’informations, consultez [Programmation de la validation](#programming).  
  
7. Pour tester l’extension, consultez [Débogage de la validation de couche](#debugging).  
  
    > [!NOTE]
    >  Votre méthode est appelée uniquement dans des circonstances spécifiques et les points d’arrêt ne fonctionnent pas automatiquement. Pour plus d’informations, consultez [Débogage de la validation de couche](#debugging).  
  
8. Pour installer l’extension VSIX dans l’instance principale de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ou sur un autre ordinateur, recherchez le fichier **.vsix** dans le répertoire **bin** du projet VSIX. Copiez-le sur l’ordinateur sur lequel vous souhaitez installer l’extension VSIX. Double-cliquez sur le fichier VSIX dans l’Explorateur Windows. (Explorateur de fichiers dans Windows 8).  
  
     Pour le désinstaller, utilisez **Extensions et mises à jour** dans le menu **Outils** .  
  
## <a name="programming"></a> Programmation de la validation  
 Pour définir une extension de validation de couche, définissez une classe avec les caractéristiques suivantes :  
  
- La forme générale de la déclaration se présente comme suit :  
  
  ```  
  
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
  >  N’utilisez pas les paramètres facultatifs de `LogValidationError`.  
  
  Quand l’utilisateur appelle la commande de menu **Valider l’architecture** , le système runtime de couche analyse les couches et leurs artefacts pour produire un graphique. Le graphique se compose de quatre parties :  
  
- les modèles de couche de la solution [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] représentés sous forme de nœuds et de liens dans le graphique ;  
  
- le code, les éléments de projet et d’autres artefacts définis dans la solution et représentés sous forme de nœuds, ainsi que les liens représentant les dépendances découvertes par le processus d’analyse ;  
  
- les liens des nœuds de couche vers les nœuds d’artefact de code ;  
  
- les nœuds représentant les erreurs découvertes par le validateur.  
  
  Une fois le graphique construit, la méthode de validation standard est appelée. Quand cette opération est terminée, toutes les méthodes de validation d’extension installées sont appelées dans un ordre non spécifié. Le graphique est passé à chaque méthode `ValidateArchitecture` qui peut analyser le graphique et signaler toutes les erreurs qu’elle rencontre.  
  
> [!NOTE]
>  Cette opération diffère du processus de validation appliqué aux diagrammes UML et du processus de validation qui peut être utilisé dans des langages spécifiques à un domaine.  
  
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
  
## <a name="debugging"></a> Débogage de la validation  
 Pour déboguer votre extension de validation de couche, appuyez sur Ctrl+F5. Une instance expérimentale de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] s’ouvre. Dans cette instance, ouvrez ou créez un modèle de couche. Ce modèle doit être associé au code et doit avoir au moins une dépendance.  
  
### <a name="test-with-a-solution-that-contains-dependencies"></a>Tester avec une solution contenant des dépendances  
 La validation n’est exécutée que si les caractéristiques suivantes sont présentes :  
  
- il existe au moins un lien de dépendance sur le diagramme de couche ;  
  
- le modèle contient des couches associées aux éléments de code.  
  
  La première fois que vous démarrez une instance expérimentale de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pour tester votre extension de validation, ouvrez ou créez une solution présentant ces caractéristiques.  
  
### <a name="run-clean-solution-before-validate-architecture"></a>Exécuter la commande Nettoyer la solution avant de valider l’architecture  
 Chaque fois que vous mettez à jour votre code de validation, utilisez la commande **Nettoyer la solution** du menu **Générer** de la solution expérimentale, et ce avant de tester la commande Valider. Cette opération est nécessaire, car les résultats de la validation sont mis en cache. Si vous n’avez pas mis à jour le diagramme de couche de test ou son code, les méthodes de validation ne sont pas exécutées.  
  
### <a name="launch-the-debugger-explicitly"></a>Lancer le débogueur explicitement  
 La validation s’exécute dans un processus séparé. Par conséquent, les points d’arrêt dans votre méthode de validation ne sont pas déclenchés. Vous devez attacher explicitement le débogueur au processus après le démarrage de la validation.  
  
 Pour attacher le débogueur au processus de validation, insérez un appel à `System.Diagnostics.Debugger.Launch()` au début de votre méthode de validation. Quand la boîte de dialogue de débogage s’affiche, sélectionnez l’instance principale de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Vous pouvez également insérer un appel à `System.Windows.Forms.MessageBox.Show()`. Quand la boîte de message s’affiche, accédez à l’instance principale de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] et, dans le menu **Déboguer** , cliquez sur **Attacher au processus**. Sélectionnez le processus nommé **Graphcmd.exe**.  
  
 Démarrez toujours l’instance expérimentale en appuyant sur Ctrl+F5 (**Exécuter sans débogage**).  
  
### <a name="deploying-a-validation-extension"></a>Déploiement d’une extension de validation  
 Pour installer votre extension de validation sur un ordinateur sur lequel une version appropriée de Visual Studio est installée, ouvrez le fichier VSIX sur l’ordinateur cible. Pour l’installer sur un ordinateur sur lequel [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] est installé, vous devez extraire manuellement le contenu du fichier VSIX dans un dossier Extensions. Pour plus d’informations, consultez [déployer une extension de modèle de couche](../modeling/deploy-a-layer-model-extension.md).  
  
## <a name="example"></a> Example code  
  
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
 [Étendre des diagrammes de couche](../modeling/extend-layer-diagrams.md)
