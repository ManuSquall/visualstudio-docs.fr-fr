---
title: Cadre d’extéabilité géré dans l’éditeur ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 888c5206b87079cf9fa91cb68e9801cb3c4f8c1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702867"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Cadre d’extéabilité géré dans l’éditeur
L’éditeur est construit en utilisant des composants du Cadre d’Extésensabilité gérée (MEF). Vous pouvez construire vos propres composants MEF pour étendre l’éditeur, et votre code peut consommer des composants d’éditeur ainsi.

## <a name="overview-of-the-managed-extensibility-framework"></a>Aperçu du Cadre d’extéponsabilité gérée
 Le MEF est une bibliothèque .NET qui vous permet d’ajouter et de modifier les fonctionnalités d’une application ou d’un composant qui suit le modèle de programmation MEF. L’éditeur Visual Studio peut à la fois fournir et consommer des composants MEF.

 Le MEF est contenu dans la version cadre .NET 4 *System.ComponentModel.Composition.dll* assemblage.

 Pour plus d’informations sur le MEF, voir [Cadre d’exténuabilité gérée (MEF)](/dotnet/framework/mef/index).

### <a name="component-parts-and-composition-containers"></a>Pièces de composants et contenants de composition
 Une partie composante est une classe ou un membre d’une classe qui peut faire un (ou les deux) des éléments suivants :

- Consommer un autre composant

- Être consommé par un autre composant

  Par exemple, envisagez une demande d’achat qui comporte un composant d’entrée de commande qui dépend des données de disponibilité des produits fournies par un composant d’inventaire d’entrepôt. En termes de MEF, la partie d’inventaire peut *exporter des* données de disponibilité des produits, et la partie de prise de commande peut *importer* les données. La partie de la prise de commande et la partie d’inventaire n’ont pas à se connaître; le *conteneur de composition* (fourni par la demande d’hôte) est chargé de maintenir l’ensemble des exportations et de résoudre les exportations et les importations.

  Le récipient <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>de composition, , est généralement la propriété de l’hôte. Le récipient de composition maintient un *catalogue* de composants exportés.

### <a name="export-and-import-component-parts"></a>Pièces de composants d’exportation et d’importation
 Vous pouvez exporter n’importe quelle fonctionnalité, tant qu’elle est implémentée en tant que classe publique ou membre public d’une classe (propriété ou méthode). Vous n’avez pas à <xref:System.ComponentModel.Composition.Primitives.ComposablePart>tirer votre partie composant de . Au lieu de <xref:System.ComponentModel.Composition.ExportAttribute> cela, vous devez ajouter un attribut à la classe ou au membre de la classe que vous voulez exporter. Cet attribut spécifie le *contrat* par lequel une autre partie composant peut importer votre fonctionnalité.

### <a name="the-export-contract"></a>Le contrat d’exportation
 Le <xref:System.ComponentModel.Composition.ExportAttribute> définit l’entité (classe, interface ou structure) qui est exportée. En règle générale, l’attribut d’exportation prend un paramètre qui spécifie le type d’exportation.

```
[Export(typeof(ContentTypeDefinition))]
class TestContentTypeDefinition : ContentTypeDefinition {   }
```

 Par défaut, <xref:System.ComponentModel.Composition.ExportAttribute> l’attribut définit un contrat qui est le type de la classe d’exportation.

```
[Export]
[Name("Structure")]
[Order(After = "Selection", Before = "Text")]
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }
```

 Dans l’exemple, `[Export]` l’attribut `[Export(typeof(TestAdornmentLayerDefinition))]`par défaut est équivalent à .

 Vous pouvez également exporter une propriété ou une méthode, comme le montre l’exemple suivant.

```
[Export]
[Name("Scarlet")]
[Order(After = "Selection", Before = "Text")]
public AdornmentLayerDefinition scarletLayerDefinition;
```

### <a name="import-a-mef-export"></a>Importer un MEF Export
 Lorsque vous voulez consommer une exportation MEF, vous devez connaître le contrat (généralement <xref:System.ComponentModel.Composition.ImportAttribute> le type) par lequel il a été exporté, et ajouter un attribut qui a cette valeur. Par défaut, l’attribut d’importation prend un paramètre, qui est le type de la classe qu’il modifie. Les lignes de code <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> suivantes importent le type.

```
[Import]
internal IClassificationTypeRegistryService ClassificationRegistry;
```

## <a name="get-editor-functionality-from-a-mef-component-part"></a>Obtenez la fonctionnalité de l’éditeur à partir d’une partie composante MEF
 Si votre code existant est une partie composante MEF, vous pouvez utiliser des métadonnées MEF pour consommer des composants d’éditeur.

#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Consommer la fonctionnalité de l’éditeur à partir d’une partie composante MEF

1. Ajoutez des références à *System.Composition.ComponentModel.dll*, qui est dans le cache d’assemblage global (GAC), et aux assemblées de l’éditeur.

2. Ajouter les directives pertinentes.

    ```
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text;
    ```

3. Ajoutez `[Import]` l’attribut à votre interface de service, comme suit.

    ```
    [Import]
    ITextBufferFactoryService textBufferService;
    ```

4. Lorsque vous avez obtenu le service, vous pouvez consommer l’un de ses composants.

5. Lorsque vous avez compilé votre assemblage, mettez-le dans le . \* Dossier de composants 'Common7'IDE' de votre installation Visual Studio.

## <a name="see-also"></a>Voir aussi
- [Service linguistique et points d’extension de l’éditeur](../extensibility/language-service-and-editor-extension-points.md)
