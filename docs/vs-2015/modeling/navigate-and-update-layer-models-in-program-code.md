---
title: Parcourir et mettre à jour les modèles de couche dans le code de programme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer models, navigating in program code
- layer models, updating in program code
ms.assetid: c60edc87-33ee-4964-a954-40069f9febf3
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 88ab52f1b06e6a2da94d17225bdb26ecec358a6c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668569"
---
# <a name="navigate-and-update-layer-models-in-program-code"></a>Parcourir et mettre à jour les modèles de couche dans le code de programme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette rubrique décrit les éléments et les relations au sein des modèles de couche, que vous pouvez parcourir et mettre à jour à l'aide de code de programme. Pour plus d’informations sur les diagrammes de couche du point de vue de l’utilisateur, consultez [diagrammes de couche : références](../modeling/layer-diagrams-reference.md) et [diagrammes de couche : instructions](../modeling/layer-diagrams-guidelines.md).

 Le modèle `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer` décrit dans cette rubrique rappelle le modèle plus général <xref:Microsoft.VisualStudio.GraphModel>. Si vous écrivez une [commande de menu ou une extension de mouvement](../modeling/add-commands-and-gestures-to-layer-diagrams.md), utilisez le `Layer` modèle. Si vous écrivez une [extension de validation de couche](../modeling/add-custom-architecture-validation-to-layer-diagrams.md), il est plus facile d’utiliser `GraphModel` .

## <a name="transactions"></a>Transactions
 Quand il s'agit de mettre à jour un modèle, enserrez les modifications dans `ILinkedUndoTransaction`. Cela permet de regrouper les modifications dans une même transaction. En cas d'échec d'une des modifications, l'ensemble de la transaction est annulée. Si l'utilisateur annule une modification, toutes les modifications sont annulées.

 Pour plus d’informations, consultez [lier des mises à jour de modèle UML à l’aide de transactions](../modeling/link-uml-model-updates-by-using-transactions.md).

```
using (ILinkedUndoTransaction t =
        LinkedUndoContext.BeginTransaction("a name"))
{
    // Make changes here ....
    t.Commit(); // Don't forget this!
}
```

## <a name="containment"></a>Containment
 ![ILayer et ILayerModel peuvent tous les deux contenir ILayers.](../modeling/media/layerapi-containment.png "LayerApi_Containment")

 Les couches ([ILayer](/previous-versions/ff644251(v=vs.140))) et le modèle de couche ([ILayerModel](/previous-versions/ff643069(v=vs.140))) peuvent contenir des commentaires et des couches.

 Une couche (`ILayer`) peut être contenue dans un modèle de couche (`ILayerModel`) ou imbriquée dans une autre couche `ILayer`.

 Pour créer un commentaire ou une couche, utilisez les méthodes de création dans le conteneur approprié.

## <a name="dependency-links"></a>Liens de dépendance
 Un lien de dépendance est représenté par un objet. Il peut être parcouru dans chaque direction :

 ![Un ILayerDependencyLink connecte deux ILayers.](../modeling/media/layerapi-dependency.png "LayerApi_Dependency")

 Pour créer un lien de dépendance, appelez `source.CreateDependencyLink(target)`.

## <a name="comments"></a>Commentaires
 Les commentaires peuvent être contenus à l'intérieur de couches ou du modèle de couche, mais aussi être liés à n'importe quel élément de couche :

 ![Les commentaires peuvent être attachés à tout élément de couche.](../modeling/media/layerapi-comments.png "LayerApi_Comments")

 Un commentaire peut être lié à autant d'éléments que nécessaire, voire à aucun.

 Pour obtenir les commentaires joints à un élément de couche, utilisez :

```csharp
ILayerModel model = diagram.GetLayerModel();
IEnumerable<ILayerComment> comments =
   model.Comments.Where(comment =>
      comment.Links.Any(link => link.Target == layerElement));

```

> [!CAUTION]
> La propriété `Comments` d'une couche `ILayer` obtient les commentaires contenus dans cette couche `ILayer`. Elle n'obtient pas les commentaires qui lui sont liés.

 Créez un commentaire en appelant `CreateComment()` dans le conteneur approprié.

 Créez un lien en utilisant `CreateLink()` dans le commentaire.

## <a name="layer-elements"></a>Éléments de couche
 Tous les types d'élément qui peuvent être contenus dans un modèle sont des éléments de couche :

 ![Les ILayerElements constituent le contenu du diagramme de couche.](../modeling/media/layerapi-layerelements.png "LayerApi_LayerElements")

## <a name="properties"></a>Propriétés
 À chaque `ILayerElement` correspond un dictionnaire de chaînes nommé `Properties`. Vous pouvez utiliser ce dictionnaire pour joindre des informations arbitraires à n'importe quel élément de couche.

## <a name="artifact-references"></a>Références d'artefact
 Une référence d’artefact ([ILayerArtifactReference](/previous-versions/ff644536(v=vs.140))) représente le lien entre une couche et un élément de projet, tel qu’un fichier, une classe ou un dossier. L'utilisateur crée des artefacts quand il crée une couche ou y ajoute des éléments en les faisant glisser depuis l'Explorateur de solutions, l'affichage de classes ou l'Explorateur d'objets vers un diagramme de couche. Il est possible de lier à une couche autant de références d'artefact que nécessaire.

 Chaque ligne figurant dans l’Explorateur de couches affiche une référence d’artefact. Pour plus d’informations, consultez [créer des diagrammes de couche à partir de votre code](../modeling/create-layer-diagrams-from-your-code.md).

 Les types et les méthodes de principal concernés par les références d'artefact sont les suivants :

 [ILayerArtifactReference](/previous-versions/ff644536(v=vs.140)). La propriété Categories indique le type d’artefact référencé (par exemple, une classe, un fichier exécutable ou un assembly). Categories détermine comment Identifier identifie l’artefact cible.

 [ArtifactReferenceExtensions. CreateArtifactReferenceAsync](/previous-versions/ff695840(v=vs.140)) crée une référence d’artefact à partir d’un ou d’un <xref:EnvDTE.Project> <xref:EnvDTE.ProjectItem> . S'agissant d'une opération asynchrone, vous fournissez généralement un rappel qui est appelé dès que la création est terminée.

 Les références d’artefact de couche ne doivent pas être confondues avec les artefacts présents dans les diagrammes de cas d’usage.

## <a name="shapes-and-diagrams"></a>Formes et diagrammes
 Deux objets sont utilisés pour représenter chaque élément dans un modèle de couche : un `ILayerElement` et un [IShape](/previous-versions/ee806673(v=vs.140)). `IShape` représente la position et la taille de la forme dans le diagramme. Dans les modèles de couche, à chaque `ILayerElement` correspond un `IShape`, et à chaque `IShape` présent dans un diagramme de couche correspond un `ILayerElement`. `IShape` est aussi utilisé avec les modèles UML. Ainsi, tous les `IShape` ne possèdent pas nécessairement un élément de couche.

 De la même manière, `ILayerModel` est affiché sur un [IDiagram](/previous-versions/ee789658(v=vs.140)).

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

 ![Chaque ILayerElement est présenté par un IShape.](../modeling/media/layerapi-shapes.png)

 [IShape](/previous-versions/ee806673(v=vs.140)) et [IDiagram](/previous-versions/ee789658(v=vs.140)) sont également utilisés pour afficher des modèles UML. Pour plus d’informations, consultez [afficher un modèle UML sur des diagrammes](../modeling/display-a-uml-model-on-diagrams.md).

## <a name="see-also"></a>Voir aussi

- [Ajouter des commandes et des mouvements aux diagrammes de couche](../modeling/add-commands-and-gestures-to-layer-diagrams.md)
- [Ajouter une validation d'architecture personnalisée aux diagrammes de couche](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)
- [Ajouter des propriétés personnalisées à des diagrammes de couche](../modeling/add-custom-properties-to-layer-diagrams.md)
- [Informations de référence sur les diagrammes de couche](../modeling/layer-diagrams-reference.md)
- [Diagrammes de couche : recommandations](../modeling/layer-diagrams-guidelines.md)
- [Étendre des diagrammes et des modèles UML](../modeling/extend-uml-models-and-diagrams.md)
