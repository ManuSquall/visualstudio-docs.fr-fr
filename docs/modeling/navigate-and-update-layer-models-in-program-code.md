---
title: "Accéder et mettre à jour des modèles de couche dans le code de programme | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- layer models, navigating in program code
- layer models, updating in program code
ms.assetid: c60edc87-33ee-4964-a954-40069f9febf3
caps.latest.revision: 20
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: fd26c504273cae739ccbeef5e406891def732985
ms.openlocfilehash: 626fc2b217285ae0c79dbd57f925281e10a0efbb
ms.lasthandoff: 02/22/2017

---
# <a name="navigate-and-update-layer-models-in-program-code"></a>Parcourir et mettre à jour les modèles de couche dans le code de programme
Cette rubrique décrit les éléments et les relations au sein des modèles de couche, que vous pouvez parcourir et mettre à jour à l'aide de code de programme. Pour plus d’informations sur les diagrammes de dépendance du point de vue de l’utilisateur, consultez la page [des diagrammes de dépendance : référence](../modeling/layer-diagrams-reference.md) et [des diagrammes de dépendance : les instructions](../modeling/layer-diagrams-guidelines.md).  
  
 Le <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer>modèle décrit dans cette rubrique est une façade plus général <xref:Microsoft.VisualStudio.GraphModel>modèle.</xref:Microsoft.VisualStudio.GraphModel> </xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer> Si vous écrivez un [extension de mouvements ou de commandes de menu](../modeling/add-commands-and-gestures-to-layer-diagrams.md), utilisez la `Layer` modèle. Si vous écrivez un [extension de validation de couche](../modeling/add-custom-architecture-validation-to-layer-diagrams.md), il est plus facile d’utiliser le `GraphModel`.  
  
## <a name="transactions"></a>Transactions  
 Quand il s'agit de mettre à jour un modèle, enserrez les modifications dans `ILinkedUndoTransaction`. Cela permet de regrouper les modifications dans une même transaction. En cas d'échec d'une des modifications, l'ensemble de la transaction est annulée. Si l'utilisateur annule une modification, toutes les modifications sont annulées.  
  
```  
using (ILinkedUndoTransaction t =  
        LinkedUndoContext.BeginTransaction("a name"))  
{   
    // Make changes here ....  
    t.Commit(); // Don't forget this!  
}  
```  
  
## <a name="containment"></a>Imbrication  
 ![ILayer et ILayerModel peuvent tous deux contenir ILayers. ] (../modeling/media/layerapi_containment.png "LayerApi_Containment")  
  
 Couches (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayer>) et le modèle de couche (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel>) peut contenir des commentaires et des couches.</xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel> </xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayer>  
  
 Une couche (`ILayer`) peut être contenue dans un modèle de couche (`ILayerModel`) ou imbriquée dans une autre couche `ILayer`.  
  
 Pour créer un commentaire ou une couche, utilisez les méthodes de création dans le conteneur approprié.  
  
## <a name="dependency-links"></a>Liens de dépendance  
 Un lien de dépendance est représenté par un objet. Il peut être parcouru dans chaque direction :  
  
 ![Un ILayerDependencyLink connecte deux ILayers. ] (../modeling/media/layerapi_dependency.png "LayerApi_Dependency")  
  
 Pour créer un lien de dépendance, appelez `source.CreateDependencyLink(target)`.  
  
## <a name="comments"></a>Commentaires  
 Les commentaires peuvent être contenus à l'intérieur de couches ou du modèle de couche, mais aussi être liés à n'importe quel élément de couche :  
  
 ![Les commentaires peuvent être attachés à tout élément de couche. ] (../modeling/media/layerapi_comments.png "LayerApi_Comments")  
  
 Un commentaire peut être lié à autant d'éléments que nécessaire, voire à aucun.  
  
 Pour obtenir les commentaires joints à un élément de couche, utilisez :  
  
```c#  
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
  
 ![les ILayerElements constituent le contenu du diagramme de dépendances. ] (../modeling/media/layerapi_layerelements.png "LayerApi_LayerElements")  
  
## <a name="properties"></a>Propriétés  
 À chaque `ILayerElement` correspond un dictionnaire de chaînes nommé `Properties`. Vous pouvez utiliser ce dictionnaire pour joindre des informations arbitraires à n'importe quel élément de couche.  
  
## <a name="artifact-references"></a>Références d’artefact  
 Une référence d’artefact (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference>) représente le lien entre une couche et un élément de projet tel qu’un fichier, une classe ou un dossier.</xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference> L’utilisateur crée des artefacts de créer une couche ou ajouter en faisant glisser des éléments depuis l’Explorateur de solutions, affichage de classes ou Explorateur d’objets dans un diagramme de dépendance. Il est possible de lier à une couche autant de références d’artefact que nécessaire.  
  
 Chaque ligne figurant dans l’Explorateur de couches affiche une référence d’artefact. Pour plus d’informations, consultez [créer des diagrammes de dépendance à partir de votre code](../modeling/create-layer-diagrams-from-your-code.md).  
  
 Les types et les méthodes de principal concernés par les références d’artefact sont les suivants :  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference>.</xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference> La propriété Categories indique le type d’artefact référencé (par exemple, une classe, un fichier exécutable ou un assembly). Categories détermine comment Identifier identifie l’artefact cible.  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ArtifactReferenceExtensions.CreateArtifactReferenceAsync%2A>Crée une référence d’artefact à partir d’un <xref:EnvDTE.Project>ou <xref:EnvDTE.ProjectItem>.</xref:EnvDTE.ProjectItem> </xref:EnvDTE.Project></xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ArtifactReferenceExtensions.CreateArtifactReferenceAsync%2A> S'agissant d'une opération asynchrone, vous fournissez généralement un rappel qui est appelé dès que la création est terminée.  
  
 Les références d'artefact de couche ne doivent pas être confondues avec les artefacts présents dans les diagrammes de cas d'usage.  
  
## <a name="shapes-and-diagrams"></a>Formes et diagrammes  
 Deux objets sont utilisés pour représenter chaque élément dans un modèle de couche : un <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement>et un <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape>.</xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape> </xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement> 
          `IShape` représente la position et la taille de la forme dans le diagramme. Dans les modèles de couche, chaque `ILayerElement` a un `IShape`et chaque `IShape` sur une dépendance de schéma a un `ILayerElement`. `IShape` est aussi utilisé avec les modèles UML. Ainsi, tous les `IShape` ne possèdent pas nécessairement un élément de couche.  
  
 De la même manière, l' <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel>est affiché dans un <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram>.</xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram> </xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel>  
  
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
  
 ![Chaque ILayerElement est présenté par un IShape. ] (~/modeling/media/layerapi_shapes.png "LayerApi_Shapes")  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape>et <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram>sont également utilisés pour afficher les modèles UML.</xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram></xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape> Pour plus d’informations, consultez [afficher un modèle UML sur des diagrammes](../modeling/display-a-uml-model-on-diagrams.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter des commandes et mouvements aux diagrammes de dépendance](../modeling/add-commands-and-gestures-to-layer-diagrams.md)   
 [Ajouter une validation d’architecture personnalisée aux diagrammes de dépendance](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)   
 [Ajouter des propriétés personnalisées aux diagrammes de dépendance](../modeling/add-custom-properties-to-layer-diagrams.md)   
 [Diagrammes de dépendance : référence](../modeling/layer-diagrams-reference.md)   
 [Diagrammes de dépendance : instructions](../modeling/layer-diagrams-guidelines.md)   

