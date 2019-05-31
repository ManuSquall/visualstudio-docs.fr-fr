---
title: Définir des contraintes de validation pour les modèles UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, validation constraints
ms.assetid: 87b3b0da-122d-4121-9318-200c38ff49d0
caps.latest.revision: 49
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4107a5fb88392f9d02cca8f41b0f53d5844d9490
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63422721"
---
# <a name="define-validation-constraints-for-uml-models"></a>Définir des contraintes de validation pour les modèles UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez définir des contraintes de validation qui vérifient si le modèle remplit une condition spécifiée. Par exemple, vous pouvez définir une contrainte pour vous assurer qu’un utilisateur ne crée pas de boucle de relations d’héritage. La contrainte, qui est appelée quand l’utilisateur essaie d’ouvrir ou d’enregistrer le modèle, peut également être appelée manuellement. Si la contrainte échoue, un message d’erreur que vous définissez est ajouté à la fenêtre d’erreur. Vous pouvez empaqueter ces contraintes dans une extension d’intégration Visual Studio ([VSIX](http://go.microsoft.com/fwlink/?LinkId=160780)) et la distribuer à d’autres utilisateurs de Visual Studio.  
  
 Vous pouvez également définir des contraintes qui valident le modèle par rapport à des ressources externes telles que des bases de données. Si vous souhaitez valider le code de programme par rapport à un diagramme de couche, consultez [ajouter la validation d’architecture personnalisée aux diagrammes de couche](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).  
  
 Pour connaître les versions de Visual Studio qui prennent en charge les modèles UML, consultez [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="requirements"></a>Configuration requise  
 Consultez [Spécifications](../modeling/extend-uml-models-and-diagrams.md#Requirements).  
  
 Pour connaître les versions de Visual Studio qui prennent en charge cette fonctionnalité, consultez [Prise en charge des versions pour les outils d'architecture et de modélisation](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="applying-validation-constraints"></a>Application de contraintes de validation  
 Les contraintes de validation sont appliquées dans trois cas : quand vous enregistrez un modèle, quand vous ouvrez un modèle et quand vous cliquez sur **Valider le modèle UML** dans le menu **Architecture** . Dans chaque cas, seules les contraintes qui ont été définies pour ce cas sont appliquées, bien qu’en général vous définissez chaque contrainte pour qu’elle s’applique dans plusieurs cas.  
  
 Les erreurs de validation sont signalées dans la fenêtre d’erreurs de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] et vous pouvez double-cliquer sur l’erreur pour sélectionner les éléments de modèle concernés.  
  
 Pour plus d’informations sur l’application de la validation, consultez [valider votre modèle UML](../modeling/validate-your-uml-model.md).  
  
## <a name="defining-a-validation-extension"></a>Définition d’une extension de validation  
 Pour créer une extension de validation pour un concepteur UML, vous devez créer une classe qui définit les contraintes de validation et incorporer cette classe dans une Extension d’intégration Visual Studio (VSIX). Cette dernière joue le rôle de conteneur capable d’installer la contrainte. Deux autres méthodes permettent de définir une extension de validation :  
  
- **Créer une extension de validation dans son propre VSIX à l’aide d’un modèle de projet.** . Il s’agit de la méthode la plus rapide. Adoptez-la si vous ne souhaitez pas combiner vos contraintes de validation avec d’autres types d’extensions, telles que les commandes de menu, les éléments de boîte à outils personnalisés ou les gestionnaires de mouvements. Vous pouvez définir plusieurs contraintes dans une classe.  
  
- **Créer des projets VSIX et classe de validation distincte.** . Choisissez cette méthode si vous souhaitez combiner plusieurs types d’extensions au sein d’un même VSIX. Par exemple, si votre commande de menu prévoit que le modèle observe des contraintes spécifiques, vous pouvez l’incorporer à la même extension VSIX en tant que méthode de validation.  
  
#### <a name="to-create-a-validation-extension-in-its-own-vsix"></a>Pour créer une extension de validation dans sa propre extension VSIX  
  
1. Dans la boîte de dialogue **Nouveau projet** , sous **Projets de modélisation**, cliquez sur **Extension de validation**.  
  
2. Ouvrez le fichier **.cs** dans le nouveau projet et modifiez la classe pour implémenter votre contrainte de validation.  
  
    Pour plus d’informations, consultez [Évaluation de la contrainte de validation](#Implementing).  
  
   > [!IMPORTANT]
   > Assurez-vous que vos fichiers **.cs** contiennent l’instruction `using` suivante :  
   >   
   >  `using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;`  
  
3. Vous pouvez ajouter des contraintes supplémentaires en définissant de nouvelles méthodes. Pour identifier une méthode comme méthode de validation, vous devez la marquer avec des attributs de la même façon que la méthode de validation initiale.  
  
4. Testez vos contraintes en appuyant sur F5. Pour plus d’informations, consultez [Exécution d’une contrainte de validation](#Executing).  
  
5. Installer la commande de menu sur un autre ordinateur en copiant le fichier **bin\\\*\\\*.vsix** qui est généré par votre projet. Pour plus d’informations, consultez [Installation et désinstallation d’une extension](#Installing).  
  
   Lors de l’ajout d’autres fichiers **.cs** , les instructions `using` suivantes sont généralement nécessaires :  
  
```csharp  
using System.Collections.Generic;  
using System.ComponentModel.Composition;  
using System.Linq;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.Modeling.Validation;  
using Microsoft.VisualStudio.Uml.Classes;  
  
```  
  
 Voici une autre procédure :  
  
#### <a name="to-create-a-separate-validation-constraint-in-a-class-library-project"></a>Pour créer une contrainte de validation distincte dans un projet de bibliothèque de classes  
  
1. Créez un projet de bibliothèque de classes en l’ajoutant à une solution VSIX existante ou en créant une solution.  
  
    1. Dans le menu **Fichier** , choisissez **Nouveau**, **Projet**.  
  
    2. Sous **Modèles installés**, développez **Visual C#** ou **Visual Basic**puis, dans la colonne du milieu, choisissez **Bibliothèque de classes**.  
  
2. Créez un projet VSIX, sauf si votre solution en comporte déjà un :  
  
    1. Dans l’ **Explorateur de solutions**, dans le menu contextuel de la solution, choisissez  **Ajouter**, puis **Nouveau projet**.  
  
    2. Sous **Modèles installés**, développez **Visual C#** ou **Visual Basic**, puis sélectionnez **Extensibilité**. Dans la colonne du milieu, cliquez sur **Projet VSIX**.  
  
3. Définissez le projet VSIX comme projet de démarrage de la solution.  
  
    - Dans l’Explorateur de solutions, dans le menu contextuel du projet VSIX, choisissez **Définir comme projet de démarrage**.  
  
4. Dans **source.extension.vsixmanifest**, sous **Contenu**, ajoutez le projet de bibliothèque de classes en tant que composant MEF :  
  
    1. Sous l’onglet **Métadonnées** , nommez le VSIX.  
  
    2. Sous l’onglet **Cibles d’installation** , définissez les versions de Visual Studio comme cibles.  
  
    3. Sous l’onglet **Composants** , choisissez **Nouveau**puis, dans la boîte de dialogue, définissez :  
  
         **Type** = **Composant MEF**  
  
         **Source** = **Projet dans la solution actuelle**  
  
         **Projet** = *Votre projet de bibliothèque de classes*  
  
#### <a name="to-define-the-validation-class"></a>Pour définir la classe de validation  
  
1. Cette procédure est inutile si vous avez créé une classe de validation avec sa propre extension VSIX à partir du modèle de projet de validation.  
  
2. Dans le projet de classe de validation, ajoutez des références aux assemblys [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] suivants :  
  
     `Microsoft.VisualStudio.Modeling.Sdk.[version]`  
  
     `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml`  
  
     `Microsoft.VisualStudio.Uml.Interfaces`  
  
     `System.ComponentModel.Composition`  
  
3. Ajoutez un fichier au projet de bibliothèque de classes contenant du code semblable à l’exemple suivant.  
  
    - Chaque contrainte de validation est contenue dans une méthode marquée avec un attribut spécifique. La méthode accepte un paramètre d’un type d’élément de modèle. Quand la validation est appelée, l’infrastructure de validation applique chaque méthode de validation à chaque élément de modèle conforme à son type de paramètre.  
  
    - Vous pouvez placer ces méthodes dans n’importe quels classes et espaces de noms. Modifiez-les à votre convenance.  
  
    ```  
    using System.Collections.Generic;  
    using System.ComponentModel.Composition;  
    using System.Linq;  
    using Microsoft.VisualStudio.Modeling.Validation;  
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
    using Microsoft.VisualStudio.Uml.Classes;  
    // You might also need the other Microsoft.VisualStudio.Uml namespaces.  
  
    namespace Validation  
    {  
      public class MyValidationExtensions  
      {  
        // SAMPLE VALIDATION METHOD.  
        // All validation methods have the following attributes.  
        [Export(typeof(System.Action<ValidationContext, object>))]  
        [ValidationMethod(  
           ValidationCategories.Save  
         | ValidationCategories.Open  
         | ValidationCategories.Menu)]  
        public void ValidateClassNames  
          (ValidationContext context,   
           // This type determines what elements   
           // will be validated by this method:  
           IClass elementToValidate)  
        {  
          // A validation method should not change the model.  
  
          List<string> attributeNames = new List<string>();  
          foreach (IProperty attribute in elementToValidate.OwnedAttributes)  
          {  
            string name = attribute.Name;  
            if (!string.IsNullOrEmpty(name) && attributeNames.Contains(name))  
            {  
              context.LogError(  
                string.Format("Duplicate attribute name '{0}' in class {1}", name, elementToValidate.Name),  
                "001", elementToValidate);  
            }  
            attributeNames.Add(name);  
          }  
  
        }  
        // Add more validation methods for different element types.  
      }  
    }  
    ```  
  
## <a name="Executing"></a> Exécution d’une contrainte de Validation  
 À des fins de test, exécutez vos méthodes de validation en mode débogage.  
  
#### <a name="to-test-the-validation-constraint"></a>Pour tester la contrainte de validation  
  
1. Appuyez sur **F5**, ou dans le menu **Déboguer** , choisissez **Démarrer le débogage**.  
  
     Une instance expérimentale de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] démarre.  
  
     **Résolution des problèmes**: Si un nouveau [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ne démarre pas :  
  
    - Si vous avez plusieurs projets, vérifiez que le projet VSIX est défini comme projet de démarrage de la solution.  
  
    - Dans l’Explorateur de solutions, dans le menu contextuel du projet de démarrage ou du projet unique, choisissez **Propriétés**. Dans l’éditeur de propriétés du projet, sélectionnez l’onglet **Déboguer** . Assurez-vous que la chaîne dans le champ **Démarrer le programme externe** correspond au chemin d’accès complet de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], qui est en général le suivant :  
  
         `C:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\devenv.exe`  
  
2. Dans l’instance expérimentale de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ouvrez ou créez un projet de modélisation, puis ouvrez ou créez un diagramme de modélisation.  
  
3. Pour configurer un test pour l’exemple de contrainte fourni dans la section précédente  
  
    1. Ouvrez un diagramme de classes.  
  
    2. Créez une classe et ajoutez-y deux attributs qui portent le même nom.  
  
4. Dans le menu contextuel n’importe où dans le diagramme, choisissez **Valider**.  
  
5. Toutes les erreurs dans le modèle seront signalées dans la fenêtre des erreurs.  
  
6. Double-cliquez sur le rapport d’erreurs. Si les éléments mentionnés dans le rapport sont visibles à l’écran, ils sont mis en surbrillance.  
  
     **Résolution des problèmes**: Si le **Validate** commande n’apparaît pas dans le menu, vérifiez que :  
  
    - le projet de validation est répertorié en tant que composant MEF sous l’onglet **Composants** de **source.extensions.manifest** dans le projet VSIX ;  
  
    - les attributs `Export` et `ValidationMethod` corrects sont associés aux méthodes de validation ;  
  
    - `ValidationCategories.Menu` est inclus dans l’argument pour le `ValidationMethod` attribut et il est composé d’autres valeurs à l’aide d’opérateur logique OR (&#124;).  
  
    - Les paramètres de tous les attributs `Import` et `Export` sont valides.  
  
## <a name="Implementing"></a> Évaluation de la contrainte  
 La méthode de validation doit déterminer si la contrainte de validation que vous souhaitez appliquer est true ou false. Si la valeur est true, elle ne doit rien faire. Si la valeur est false, elle doit signaler une erreur à l’aide des méthodes fournies par le paramètre `ValidationContext` .  
  
> [!NOTE]
> Les méthodes de validation ne doivent pas changer le modèle. Le moment et l’ordre d’exécution des contraintes ne sont pas garantis. Si vous devez passer des informations entre des exécutions consécutives d’une méthode de validation lors d’une série de validation, vous pouvez utiliser le cache de contexte décrit dans [Coordination de plusieurs validations](#ContextCache).  
  
 Par exemple, si vous souhaitez vous assurer que chaque type (classe, interface ou énumérateur) possède un nom comportant au moins trois caractères, vous pouvez utiliser cette méthode :  
  
```  
public void ValidateTypeName(ValidationContext context, IType type)  
{  
  if (!string.IsNullOrEmpty(type.Name) && type.Name.Length < 3)  
  {  
    context.LogError(  
      string.Format("Type name {0} is too short", type.Name),  
               "001", type);  
   }  
 }  
```  
  
 Pour plus d’informations sur les méthodes et les types que vous pouvez utiliser pour parcourir et lire le modèle, consultez [Programming with the UML API](../modeling/programming-with-the-uml-api.md) .  
  
### <a name="about-validation-constraint-methods"></a>À propos des méthodes de contrainte de validation  
 Chaque contrainte de validation est définie par une méthode au format suivant :  
  
```  
[Export(typeof(System.Action<ValidationContext, object>))]  
 [ValidationMethod(ValidationCategories.Save   
  | ValidationCategories.Menu   
  | ValidationCategories.Open)]  
public void ValidateSomething  
  (ValidationContext context, IClassifier elementToValidate)  
{...}  
```  
  
 Les attributs et les paramètres de chaque méthode de validation sont les suivants :  
  
|||  
|-|-|  
|`[Export(typeof(System.Action <ValidationContext, object>))]`|Définit la méthode comme contrainte de validation à l’aide de l’infrastructure MEF (Managed Extensibility Framework).|  
|`[ValidationMethod (ValidationCategories.Menu)]`|Spécifie quand la validation est effectuée. Utilisez une opération de bits OR (&#124;) si vous souhaitez combiner plusieurs options.<br /><br /> `Menu` = appelé par le menu Valider.<br /><br /> `Save` = appelé lors de l’enregistrement du modèle.<br /><br /> `Open` = appelé lors de l’ouverture du modèle. `Load` = appelé lors de l’enregistrement du modèle, mais en cas d’infraction prévient l’utilisateur qu’il sera peut-être impossible de rouvrir le modèle. Également appelé lors du chargement, avant l’analyse du modèle.|  
|`public void ValidateSomething`<br /><br /> `(ValidationContext context,`<br /><br /> `IElement element)`|Remplacez le deuxième paramètre `IElement` par le type d’élément auquel vous souhaitez que la contrainte s’applique. La méthode de contrainte est appelée sur tous les éléments dans le type spécifié.<br /><br /> Le nom de la méthode est sans importance.|  
  
 Vous pouvez définir autant de méthodes de validation que vous le souhaitez, avec des types différents dans le deuxième paramètre. Quand la validation est appelée, chaque méthode de validation est appelée sur chaque élément de modèle conforme au type de paramètre.  
  
### <a name="reporting-validation-errors"></a>Signalement des erreurs de validation  
 Pour créer un rapport d’erreurs, utilisez les méthodes fournies par `ValidationContext`:  
  
 `context.LogError("error string", errorCode, elementsWithError);`  
  
- `"error string"` apparaît dans la liste d’erreurs de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]  
  
- `errorCode` est une chaîne qui doit être un identificateur unique de l’erreur  
  
- `elementsWithError` identifie les éléments dans le modèle. Quand l’utilisateur double-clique sur le rapport d’erreurs, la forme représentant cet élément est sélectionnée.  
  
  `LogError(),` `LogWarning()` et `LogMessage()` placent les messages dans différentes sections de la liste d’erreurs.  
  
## <a name="how-validation-methods-are-applied"></a>Application des méthodes de validation  
 La validation est appliquée à chaque élément du modèle, y compris aux relations et aux différentes parties des plus grands éléments, tels que les attributs d’une classe et les paramètres d’une opération.  
  
 Chaque méthode de validation est appliquée à chaque élément conforme au type mentionné dans son deuxième paramètre. Cela signifie par exemple que si vous définissez une méthode de validation avec un deuxième paramètre `IUseCase` et un autre avec son supertype `IElement`, ces deux méthodes sont appliquées à chaque cas d’usage dans le modèle.  
  
 La hiérarchie des types est résumée dans [types d’éléments UML modèle](../modeling/uml-model-element-types.md).  
  
 Vous pouvez également accéder aux éléments en suivant des relations. Par exemple, si vous devez définir une méthode de validation sur `IClass`, vous pouvez parcourir en boucle les propriétés dont il est propriétaire :  
  
```  
public void ValidateTypeName(ValidationContext context, IClass c)  
{  
   foreach (IProperty property in c.OwnedAttributes)  
   {  
       if (property.Name.Length < 3)  
       {  
            context.LogError(  
                 string.Format(  
                        "Property name {0} is too short",   
                        property.Name),   
                 "001", property);  
        }  
   }  
}  
```  
  
### <a name="creating-a-validation-method-on-the-model"></a>Création d’une méthode de validation sur le modèle  
 Si vous souhaitez vous assurer qu’une méthode de validation est appelée exactement une fois lors de chaque exécution de validation, vous pouvez valider le `IModel`:  
  
```  
using Microsoft.VisualStudio.Uml.AuxiliaryConstructs; ...  
[Export(typeof(System.Action<ValidationContext, object>))]  
[ValidationMethod(ValidationCategories.Menu)]  
public void ValidateModel(ValidationContext context, IModel model)  
{  foreach (IElement element in model.OwnedElements)  
   { ...  
```  
  
### <a name="validating-shapes-and-diagrams"></a>Validation de formes et de diagrammes  
 Les méthodes de validation ne sont pas appelées sur les éléments d’affichage tels que les diagrammes et les formes, car l’objectif principal des méthodes de validation consiste à valider le modèle. Vous pouvez toutefois accéder au diagramme actif à l’aide du contexte de diagramme.  
  
 Dans votre classe de validation, déclarez `DiagramContext` comme propriété importée :  
  
```  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;   
...  
[Import]  
public IDiagramContext DiagramContext { get; set; }  
```  
  
 Dans une méthode de validation, vous pouvez utiliser `DiagramContext` pour accéder au diagramme de focus actif, s’il y en a un :  
  
```  
[Export(typeof(System.Action<ValidationContext, object>))]  
[ValidationMethod(ValidationCategories.Menu)]  
public void ValidateModel(ValidationContext context, IModel model)  
{  
  IDiagram focusDiagram = DiagramContext.CurrentDiagram;  
  if (focusDiagram != null)  
  {  
    foreach (IShape<IUseCase> useCaseShape in  
              focusDiagram.GetChildShapes<IUseCase>())  
    { ...  
```  
  
 Pour consigner une erreur, vous devez obtenir l’élément de modèle représenté par la forme, car vous ne pouvez pas passer une forme à `LogError`:  
  
```  
IUseCase useCase = useCaseShape.Element;  
context.LogError(... , usecase);  
```  
  
### <a name="ContextCache"></a> Coordination de plusieurs Validations  
 Quand la validation est appelée, par exemple par l’utilisateur à partir d’un menu de diagramme, chaque méthode de validation est appliquée à chaque élément de modèle. Cela signifie que, dans un appel unique à l’infrastructure de validation, la même méthode peut être appliquée plusieurs fois à différents éléments.  
  
 Cela pose un problème pour les validations associées aux relations entre les éléments. Par exemple, vous pouvez écrire une validation qui commence à un cas d’usage et qui traverse les relations **include** pour vérifier qu’il n’y a pas de boucle. Mais quand la méthode est appliquée à chaque cas d’usage dans un modèle comportant de nombreux liens **include** , il est probable qu’elle traite à répétition les mêmes zones du modèle.  
  
 Pour éviter cette situation, il existe un cache de contexte dans lequel les informations sont conservées durant une exécution de validation. Vous pouvez l’utiliser pour passer des informations entre différentes exécutions des méthodes de validation. Par exemple, vous pouvez stocker une liste des éléments qui ont déjà été traitées lors de cette exécution de validation. Le cache est créé au début de chaque exécution de validation et vous ne pouvez pas l’utiliser pour passer des informations entre différentes exécutions de validation.  
  
|||  
|-|-|  
|`context.SetCacheValue<T> (name, value)`|Stocker une valeur|  
|`context.TryGetCacheValue<T> (name, out value)`|Obtenir une valeur. Retourne la valeur true si l’opération réussit.|  
|`context.GetValue<T>(name)`|Obtenir une valeur.|  
|`Context.GetValue<T>()`|Obtenir une valeur du type spécifié.|  
  
## <a name="Installing"></a> Installation et désinstallation d’une extension  
 Vous pouvez installer une extension [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] sur votre propre ordinateur et sur d’autres ordinateurs.  
  
#### <a name="to-install-an-extension"></a>Pour installer une extension  
  
1. Sur votre ordinateur, recherchez le fichier **.vsix** généré par votre projet VSIX.  
  
    1. Dans l’ **Explorateur de solutions**, dans le menu contextuel du projet VSIX, choisissez **Ouvrir le dossier dans l’Explorateur Windows**.  
  
    2. Recherchez le fichier **bin\\\*\\** _VotreProjet_ **.vsix**  
  
2. Copiez le fichier **.vsix** sur l’ordinateur cible sur lequel vous souhaitez installer l’extension. Il peut s’agir de votre propre ordinateur ou d’un autre.  
  
    - L’ordinateur cible doit disposer de l’une des éditions de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] que vous avez spécifiées dans **source.extension.vsixmanifest**.  
  
3. Sur l’ordinateur cible, ouvrez le fichier **.vsix** .  
  
     Le**Programme d’installation des extensions Visual Studio** s’ouvre et installe l’extension.  
  
4. Démarrez ou redémarrez [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
#### <a name="to-uninstall-an-extension"></a>Pour désinstaller une extension  
  
1. Dans le menu **Outils** , choisissez **Extensions et mises à jour**.  
  
2. Développez **Extensions installées**.  
  
3. Sélectionnez l’extension, puis choisissez **Désinstaller**.  
  
   Exceptionnellement, une extension défaillante ne parvient pas à se charger et crée un rapport dans la fenêtre d’erreur, mais ne s’affiche pas dans le Gestionnaire d’extensions. Dans ce cas, vous pouvez supprimer l’extension en supprimant le fichier à partir de l’emplacement suivant où *% LocalAppData%* est généralement *nom_lecteur*: \Users\\*nom d’utilisateur*\AppData\Local :  
  
   *%LocalAppData%* **\Microsoft\VisualStudio\\[version]\Extensions**  
  
## <a name="Example"></a> Exemple  
 Cet exemple recherche des boucles dans la relation Dependency entre les éléments.  
  
 Il effectue une validation à la fois lors de l’enregistrement et lors de l’utilisation de la commande de menu Valider.  
  
```  
/// <summary>  
/// Verify that there are no loops in the dependency relationsips.  
/// In our project, no element should be a dependent of itself.  
/// </summary>  
/// <param name="context">Validation context for logs.</param>  
/// <param name="element">Element to start validation from.</param>  
[Export(typeof(System.Action<ValidationContext, object>))]  
[ValidationMethod(ValidationCategories.Menu   
     | ValidationCategories.Save | ValidationCategories.Open)]  
public void NoDependencyLoops(ValidationContext context, INamedElement element)  
{  
    // The validation framework will call this method  
    // for every element in the model. But when we follow  
    // the dependencies from one element, we will validate others.  
    // So we keep a list of the elements that we don't need to validate again.   
    // The list is kept in the context cache so that it is passed  
    // from one execution of this method to another.  
    List<INamedElement> alreadySeen = null;  
    if (!context.TryGetCacheValue("No dependency loops", out alreadySeen))  
    {  
       alreadySeen = new List<INamedElement>();  
       context.SetCacheValue("No dependency loops", alreadySeen);  
    }  
  
    NoDependencyLoops(context, element,   
                new INamedElement[0], alreadySeen);      
}  
  
/// <summary>  
/// Log an error if there is any loop in the dependency relationship.  
/// </summary>  
/// <param name="context">Validation context for logs.</param>  
/// <param name="element">The element to be validated.</param>  
/// <param name="dependants">Elements we've followed in this recursion.</param>  
/// <param name="alreadySeen">Elements that have already been validated.</param>  
/// <returns>true if no error was detected</returns>  
private bool NoDependencyLoops(ValidationContext context,   
    INamedElement element, INamedElement[] dependants,   
    List<INamedElement> alreadySeen)  
{  
    if (dependants.Contains(element))  
    {  
        context.LogError(string.Format("{0} should not depend on itself", element.Name),   
        "Fabrikam.UML.NoGenLoops", // unique code for this error  
        dependants.SkipWhile(e => e != element).ToArray());   
            // highlight elements that are in the loop  
        return false;  
    }  
    INamedElement[] dependantsPlusElement =   
        new INamedElement[dependants.Length + 1];  
    dependants.CopyTo(dependantsPlusElement, 0);  
    dependantsPlusElement[dependantsPlusElement.Length - 1] = element;  
  
    if (alreadySeen.Contains(element))  
    {  
        // We have already validated this when we started   
        // from another element during this validation run.  
        return true;  
    }  
    alreadySeen.Add(element);  
  
    foreach (INamedElement supplier in element.GetDependencySuppliers())  
    {  
        if (!NoDependencyLoops(context, supplier,  
             dependantsPlusElement, alreadySeen))  
        return false;  
    }  
    return true;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Définir et installer une extension de modélisation](../modeling/define-and-install-a-modeling-extension.md)   
 [Programmation avec l’API UML](../modeling/programming-with-the-uml-api.md)
