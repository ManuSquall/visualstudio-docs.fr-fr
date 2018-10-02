---
title: Parcourir et mettre à jour des modèles de couche dans le code de programme | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- layer models, navigating in program code
- layer models, updating in program code
ms.assetid: c60edc87-33ee-4964-a954-40069f9febf3
caps.latest.revision: 22
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 3b4be16e9778ffe39e03e55254f6e38e64f3ad21
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47503991"
---
# <a name="navigate-and-update-layer-models-in-program-code"></a>Parcourir et mettre à jour les modèles de couche dans le code de programme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Parcourir et mise à jour des modèles dans le code de programme de couche](https://docs.microsoft.com/visualstudio/modeling/navigate-and-update-layer-models-in-program-code).  
  
Cette rubrique décrit les éléments et les relations au sein des modèles de couche, que vous pouvez parcourir et mettre à jour à l'aide de code de programme. Pour plus d’informations sur les diagrammes de couche à partir du point de vue de l’utilisateur, consultez [diagrammes de couche : référence](../modeling/layer-diagrams-reference.md) et [diagrammes de couche : instructions](../modeling/layer-diagrams-guidelines.md).  
  
 Le modèle <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer> décrit dans cette rubrique rappelle le modèle plus général <xref:Microsoft.VisualStudio.GraphModel>. Si vous écrivez un [extension de mouvements ou de commandes de menu](../modeling/add-commands-and-gestures-to-layer-diagrams.md), utilisez la `Layer` modèle. Si vous écrivez un [extension de validation de couche](../modeling/add-custom-architecture-validation-to-layer-diagrams.md), il est plus facile à utiliser le `GraphModel`.  
  
## <a name="transactions"></a>Transactions  
 Quand il s'agit de mettre à jour un modèle, enserrez les modifications dans `ILinkedUndoTransaction`. Cela permet de regrouper les modifications dans une même transaction. En cas d'échec d'une des modifications, l'ensemble de la transaction est annulée. Si l'utilisateur annule une modification, toutes les modifications sont annulées.  
  
 Pour plus d’informations, consultez [mises à jour du modèle UML de lien à l’aide de transactions](../modeling/link-uml-model-updates-by-using-transactions.md).  
  
```  
using (ILinkedUndoTransaction t =  
        LinkedUndoContext.BeginTransaction("a name"))  
{   
    // Make changes here ....  
    t.Commit(); // Don't forget this!  
}  
```  
  
## <a name="containment"></a>Imbrication  
 ![ILayer et ILayerModel peuvent tous deux contenir ILayers. ](../modeling/media/layerapi-containment.png "LayerApi_Containment")  
  
 Les couches (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayer>) et le modèle de couche (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel>) peuvent contenir des commentaires et des couches.  
  
 Une couche (`ILayer`) peut être contenue dans un modèle de couche (`ILayerModel`) ou imbriquée dans une autre couche `ILayer`.  
  
 Pour créer un commentaire ou une couche, utilisez les méthodes de création dans le conteneur approprié.  
  
## <a name="dependency-links"></a>Liens de dépendance  
 Un lien de dépendance est représenté par un objet. Il peut être parcouru dans chaque direction :  
  
 ![Un ILayerDependencyLink connecte deux ILayers. ](../modeling/media/layerapi-dependency.png "LayerApi_Dependency")  
  
 Pour créer un lien de dépendance, appelez `source.CreateDependencyLink(target)`.  
  
## <a name="comments"></a>Commentaires  
 Les commentaires peuvent être contenus à l'intérieur de couches ou du modèle de couche, mais aussi être liés à n'importe quel élément de couche :  
  
 ![Commentaires peuvent être associés à n’importe quel élément de couche. ](../modeling/media/layerapi-comments.png "LayerApi_Comments")  
  
 Un commentaire peut être lié à autant d'éléments que nécessaire, voire à aucun.  
  
 Pour obtenir les commentaires joints à un élément de couche, utilisez :  
  
```csharp  
ILayerModel model = diagram.GetLayerModel();   
IEnumerable<ILayerComment> comments =   
   model.Comments.Where(comment =>   
      comment.Links.Any(link => link.Target == layerElement));  
  
```  
  
> [!CAUTION]
>  La propriété `Comments` d'une couche `ILayer` obtient les commentaires contenus dans cette couche `ILayer`. Elle n'obtient pas les commentaires qui lui sont liés.  
  
 Créez un commentaire en appelant `CreateComment()` dans le conteneur approprié.  
  
 Créez un lien en utilisant `CreateLink()` dans le commentaire.  
  
## <a name="layer-elements"></a>Éléments de couche  
 Tous les types d'élément qui peuvent être contenus dans un modèle sont des éléments de couche :  
  
 ![Les ILayerElements constituent le contenu du diagramme de couche. ](../modeling/media/layerapi-layerelements.png "LayerApi_LayerElements")  
  
## <a name="properties"></a>Properties  
 À chaque `ILayerElement` correspond un dictionnaire de chaînes nommé `Properties`. Vous pouvez utiliser ce dictionnaire pour joindre des informations arbitraires à n'importe quel élément de couche.  
  
## <a name="artifact-references"></a>Références d'artefact  
 Une référence d'artefact (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference>) représente le lien entre une couche et un élément de projet, tel qu'un fichier, une classe ou un dossier. L'utilisateur crée des artefacts quand il crée une couche ou y ajoute des éléments en les faisant glisser depuis l'Explorateur de solutions, l'affichage de classes ou l'Explorateur d'objets vers un diagramme de couche. Il est possible de lier à une couche autant de références d'artefact que nécessaire.  
  
 Chaque ligne figurant dans l’Explorateur de couches affiche une référence d’artefact. Pour plus d’informations, consultez [créer des diagrammes de couche à partir de votre code](../modeling/create-layer-diagrams-from-your-code.md).  
  
 Les types et les méthodes de principal concernés par les références d’artefact sont les suivants :  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference>. La propriété Categories indique le type d'artefact référencé (par exemple, une classe, un fichier exécutable ou un assembly). Categories détermine comment Identifier identifie l'artefact cible.  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ArtifactReferenceExtensions.CreateArtifactReferenceAsync%2A> crée une référence d'artefact à partir de <xref:EnvDTE.Project> ou <xref:EnvDTE.ProjectItem>. S'agissant d'une opération asynchrone, vous fournissez généralement un rappel qui est appelé dès que la création est terminée.  
  
 Les références d'artefact de couche ne doivent pas être confondues avec les artefacts présents dans les diagrammes de cas d'usage.  
  
## <a name="shapes-and-diagrams"></a>Formes et diagrammes  
 Chaque élément figurant dans un modèle de couche est représenté par deux objets : <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement> et <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape>. `IShape` représente la position et la taille de la forme dans le diagramme. Dans les modèles de couche, à chaque `ILayerElement` correspond un `IShape`, et à chaque `IShape` présent dans un diagramme de couche correspond un `ILayerElement`. `IShape` est aussi utilisé avec les modèles UML. Ainsi, tous les `IShape` ne possèdent pas nécessairement un élément de couche.  
  
 De la même façon, <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel> est affiché dans un <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram>.  
  
 Dans le code d'une commande personnalisée ou d'un gestionnaire de mouvements, vous pouvez obtenir le diagramme actif et la sélection de formes active à partir de l'importation de `DiagramContext` :  
  
```  
public class ... {  
[Import]  
    public IDiagramContext DiagramContext { get; set; }  
...  
public void ... (...)   
{ IDiagram diagram = this.DiagramContext.CurrentDiagram;  
  ILayerModel model = diagram.GetLayerModel();  
  if (model != null)  
  { foreach (ILayer layer in model.Layers) { ... }}  
  foreach (IShape selected in diagram.SelectedShapes)  
  { ILayerElement element = selected.GetLayerElement();  
    if (element != null) ... }}  
```  
  
 ![Chaque ILayerElement est présenté par un IShape. ](../modeling/media/layerapi-shapes.png "LayerApi_Shapes")  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape> et <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram> sont aussi utilisés pour afficher les modèles UML. Pour plus d’informations, consultez [afficher un modèle UML sur des diagrammes](../modeling/display-a-uml-model-on-diagrams.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter des commandes et des mouvements aux diagrammes de couche](../modeling/add-commands-and-gestures-to-layer-diagrams.md)   
 [Ajouter une validation d’architecture personnalisée aux diagrammes de couche](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)   
 [Ajouter des propriétés personnalisées aux diagrammes de couche](../modeling/add-custom-properties-to-layer-diagrams.md)   
 [Diagrammes de couche : référence](../modeling/layer-diagrams-reference.md)   
 [Diagrammes de couche : instructions](../modeling/layer-diagrams-guidelines.md)   
 [Étendre des diagrammes et des modèles UML](../modeling/extend-uml-models-and-diagrams.md)



