---
title: Managed Extensibility Framework dans l’éditeur | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 41d5768c8cfddc3474616d7a2eee16b84cd24d56
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51754701"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Managed Extensibility Framework (MEF) dans l’éditeur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’éditeur est généré à l’aide des composants de Managed Extensibility Framework (MEF). Vous pouvez créer vos propres composants MEF pour étendre l’éditeur, et votre code peut consommer des composants de l’éditeur ainsi.  
  
## <a name="overview-of-the-managed-extensibility-framework"></a>Vue d’ensemble de Managed Extensibility Framework  
 MEF est une bibliothèque .NET qui vous permet d’ajouter et modifier les fonctionnalités d’une application ou un composant qui suit le modèle de programmation MEF. L’éditeur Visual Studio peut fournir et consommer des composants MEF.  
  
 MEF est contenu dans l’assembly de System.ComponentModel.Composition.dll de .NET Framework version 4.  
  
 Pour plus d’informations sur MEF, consultez [Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
### <a name="component-parts-and-composition-containers"></a>Composants et conteneurs de Composition  
 Un composant est une classe ou un membre d’une classe qui peut effectuer une des opérations suivantes (ou les deux) :  
  
- Utiliser un autre composant  
  
- Être consommé par un autre composant  
  
  Par exemple, considérez une application d’achat qui a un composant d’entrée de commande qui dépend des données de disponibilité de produit fournies par un composant de stock d’entrepôt. En termes MEF, la partie de l’inventaire peut *exporter* les données de disponibilité de produit et le peut de partie commande entrée *importer* les données. La partie entrée de commande et la partie de l’inventaire n’ont pas à connaître sur les autres ; le *conteneur de composition* (fourni par l’application hôte) est responsable en conservant le jeu d’exportations et la résolution des exportations et importations.  
  
  Le conteneur de composition, <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, est généralement détenus par l’hôte. Le conteneur de composition conserve un *catalogue* composants exporté.  
  
### <a name="exporting-and-importing-component-parts"></a>Exportation et importation de composants  
 Vous pouvez exporter toutes les fonctionnalités, tant qu’elle est implémentée comme une classe publique ou un membre public d’une classe (propriété ou méthode). Vous n’êtes pas obligé de dériver votre composant à partir de <xref:System.ComponentModel.Composition.Primitives.ComposablePart>. Au lieu de cela, vous devez ajouter un <xref:System.ComponentModel.Composition.ExportAttribute> d’attribut à la classe ou un membre de classe que vous souhaitez exporter. Cet attribut spécifie le *contrat* par le composant d’une autre partie peut importer vos fonctionnalités.  
  
### <a name="the-export-contract"></a>Le contrat d’exportation  
 Le <xref:System.ComponentModel.Composition.ExportAttribute> définit l’entité (classe, interface ou structure) qui est en cours d’exportation. En règle générale, l’attribut export prend un paramètre qui spécifie le type de l’exportation.  
  
```  
[Export(typeof(ContentTypeDefinition))]  
class TestContentTypeDefinition : ContentTypeDefinition {   }  
```  
  
 Par défaut, le <xref:System.ComponentModel.Composition.ExportAttribute> attribut définit un contrat qui est le type de la classe d’exportation.  
  
```  
[Export]  
[Name("Structure")]  
[Order(After = "Selection", Before = "Text")]  
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }  
```  
  
 Dans l’exemple, la valeur par défaut `[Export]` attribut équivaut à `[Export(typeof(TestAdornmentLayerDefinition))]`.  
  
 Vous pouvez également exporter une propriété ou méthode, comme illustré dans l’exemple suivant.  
  
```  
[Export]  
[Name("Scarlet")]  
[Order(After = "Selection", Before = "Text")]  
public AdornmentLayerDefinition scarletLayerDefinition;  
```  
  
### <a name="importing-a-mef-export"></a>L’importation d’une exportation MEF  
 Lorsque vous souhaitez consommer une exportation MEF, vous devez connaître le contrat (généralement le type) et en ce qui a été exporté, ajoutez un <xref:System.ComponentModel.Composition.ImportAttribute> attribut ayant cette valeur. Par défaut, l’attribut d’importation prend un paramètre, ce qui est le type de la classe qu’il modifie. Les lignes suivantes de l’importation de code la <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> type.  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationRegistry;  
```  
  
## <a name="getting-editor-functionality-from-a-mef-component-part"></a>Obtention des fonctionnalités de l’éditeur à partir d’un composant MEF  
 Si votre code existant est un composant MEF, vous pouvez utiliser des métadonnées MEF pour consommer des composants de l’éditeur.  
  
#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Pour utiliser la fonctionnalité d’éditeur à partir d’un composant MEF  
  
1.  Ajoutez des références à System.Composition.ComponentModel.dll, qui est dans le global assembly cache (GAC), et pour les assemblys de l’éditeur.  
  
2.  Ajouter les informations pertinentes à l’aide d’instructions.  
  
    ```  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text;  
    ```  
  
3.  Ajouter le `[Import]` attribut à votre interface de service, comme suit.  
  
    ```  
    [Import]  
    ITextBufferFactoryService textBufferService;  
    ```  
  
4.  Lorsque vous avez obtenu le service, vous pouvez utiliser l’un de ses composants.  
  
5.  Lorsque vous avez compilé votre assembly, placez-le dans le... Dossier \Common7\IDE\Components\ de votre installation de Visual Studio.  
  
## <a name="see-also"></a>Voir aussi  
 [Points d’extension du service de langage et de l’éditeur](../extensibility/language-service-and-editor-extension-points.md)

