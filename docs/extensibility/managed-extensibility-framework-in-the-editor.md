---
title: "Managed Extensibility Framework dans l’éditeur | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 6a5cb0ae0f8da6af939588ad358e6b5b1b3b108e
ms.lasthandoff: 02/22/2017

---
# <a name="managed-extensibility-framework-in-the-editor"></a>Managed Extensibility Framework dans l’éditeur
L’éditeur est construit à l’aide des composants de Managed Extensibility Framework (MEF). Vous pouvez créer vos propres composants MEF pour étendre l’éditeur, et votre code peut consommer des composants et de l’éditeur.  
  
## <a name="overview-of-the-managed-extensibility-framework"></a>Vue d’ensemble de Managed Extensibility Framework  
 MEF est une bibliothèque .NET qui vous permet d’ajouter et modifier les fonctionnalités d’une application ou un composant qui suit le modèle de programmation MEF. L’éditeur Visual Studio peut fournir et consommer des composants MEF.  
  
 MEF est contenu dans l’assembly de System.ComponentModel.Composition.dll de .NET Framework version 4.  
  
 Pour plus d’informations sur MEF, consultez [Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/Library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
### <a name="component-parts-and-composition-containers"></a>Composants et conteneurs de Composition  
 Un composant est une classe ou un membre d’une classe que vous pouvez effectuer une des opérations suivantes (ou les deux) :  
  
-   Utiliser un autre composant  
  
-   Être consommé par un autre composant  
  
 Par exemple, considérez une application d’achat qui a un composant de saisie de commande qui repose sur les données de disponibilité du produit fournies par un composant d’inventaire de l’entrepôt. En termes MEF, la partie de l’inventaire peut *exporter* les données de disponibilité de produit et les parties peuvent être commande entrée *importer* les données. La partie entrée de commande et la partie de l’inventaire n’ont pas à savoir sur l’autre ; le *conteneur de composition* (fourni par l’application hôte) est chargé de gérer l’ensemble des exportations et résolution des exportations et importations.  
  
 Le conteneur de composition, <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, est généralement détenus par l’hôte.</xref:System.ComponentModel.Composition.Hosting.CompositionContainer> Le conteneur de composition conserve un *catalogue* composants exporté.  
  
### <a name="exporting-and-importing-component-parts"></a>Exportation et importation de composants  
 Vous pouvez exporter toutes les fonctionnalités, tant qu’il est implémenté comme une classe publique ou un membre public d’une classe (propriété ou méthode). Vous n’avez pas dériver votre composant <xref:System.ComponentModel.Composition.Primitives.ComposablePart>.</xref:System.ComponentModel.Composition.Primitives.ComposablePart> Au lieu de cela, vous devez ajouter un <xref:System.ComponentModel.Composition.ExportAttribute>d’attribut à la classe ou un membre de classe que vous souhaitez exporter.</xref:System.ComponentModel.Composition.ExportAttribute> Cet attribut spécifie le *contrat* par le composant d’une autre partie peut importer votre fonctionnalité.  
  
### <a name="the-export-contract"></a>Le contrat d’exportation  
 Le <xref:System.ComponentModel.Composition.ExportAttribute>définit l’entité (classe, interface ou structure) qui est en cours d’exportation.</xref:System.ComponentModel.Composition.ExportAttribute> En règle générale, l’attribut export prend un paramètre qui spécifie le type de l’exportation.  
  
```  
[Export(typeof(ContentTypeDefinition))]  
class TestContentTypeDefinition : ContentTypeDefinition {   }  
```  
  
 Par défaut, l' <xref:System.ComponentModel.Composition.ExportAttribute>attribut définit un contrat qui est le type de la classe exportation.</xref:System.ComponentModel.Composition.ExportAttribute>  
  
```  
[Export]  
[Name("Structure")]  
[Order(After = "Selection", Before = "Text")]  
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }  
```  
  
 Dans l’exemple, la valeur par défaut `[Export]` attribut équivaut à `[Export(typeof(TestAdornmentLayerDefinition))]`.  
  
 Vous pouvez également exporter une propriété ou une méthode, comme illustré dans l’exemple suivant.  
  
```  
[Export]  
[Name("Scarlet")]  
[Order(After = "Selection", Before = "Text")]  
public AdornmentLayerDefinition scarletLayerDefinition;  
```  
  
### <a name="importing-a-mef-export"></a>L’importation d’une exportation MEF  
 Lorsque vous souhaitez consommer une exportation MEF, vous devez connaître le contrat (généralement le type) et en ce qui a été exporté, ajoutez un <xref:System.ComponentModel.Composition.ImportAttribute>attribut qui possède cette valeur.</xref:System.ComponentModel.Composition.ImportAttribute> Par défaut, l’attribut d’importation prend un paramètre, qui est le type de la classe qu’il modifie. Les lignes suivantes de l’importation de code la <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>type.</xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationRegistry;  
```  
  
## <a name="getting-editor-functionality-from-a-mef-component-part"></a>Mise en route de la fonctionnalité de l’éditeur à partir d’un composant MEF  
 Si votre code existant est un composant MEF, vous pouvez utiliser les métadonnées MEF pour consommer des composants de l’éditeur.  
  
#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Pour utiliser les fonctionnalités d’éditeur à partir d’un composant MEF  
  
1.  Ajoutez des références à System.Composition.ComponentModel.dll, qui se trouve dans le global assembly cache (GAC), et pour les assemblys de l’éditeur.  
  
2.  Ajoutez les instructions using.  
  
    ```  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text;  
    ```  
  
3.  Ajouter la `[Import]` attribut à votre interface de service, comme suit.  
  
    ```  
    [Import]  
    ITextBufferFactoryService textBufferService;  
    ```  
  
4.  Lorsque vous avez obtenu le service, vous pouvez utiliser l’un de ses composants.  
  
5.  Lorsque vous avez compilé votre assembly et placez-la dans le... Dossier \Common7\IDE\Components\ de votre installation de Visual Studio.  
  
## <a name="see-also"></a>Voir aussi  
 [Service de langage et les Points d’Extension Éditeur](../extensibility/language-service-and-editor-extension-points.md)
