---
title: Managed Extensibility Framework dans l’éditeur | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f19b71c86d972b59a9d46f379bf7ec93f63aeb9a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65679953"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Managed Extensibility Framework (MEF) dans l’éditeur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’éditeur est généré à l’aide de composants Managed Extensibility Framework (MEF). Vous pouvez créer vos propres composants MEF pour étendre l’éditeur, et votre code peut également utiliser des composants de l’éditeur.  
  
## <a name="overview-of-the-managed-extensibility-framework"></a>Vue d’ensemble de l’Managed Extensibility Framework  
 MEF est une bibliothèque .NET qui vous permet d’ajouter et de modifier les fonctionnalités d’une application ou d’un composant qui suit le modèle de programmation MEF. L’éditeur Visual Studio peut à la fois fournir et utiliser des composants MEF.  
  
 Le MEF est contenu dans le .NET Framework assembly System.ComponentModel.Composition.dll version 4.  
  
 Pour plus d’informations sur MEF, consultez [Managed Extensibility Framework (MEF)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
### <a name="component-parts-and-composition-containers"></a>Composants et conteneurs de composition  
 Une partie de composant est une classe ou un membre d’une classe qui peut effectuer l’une des opérations suivantes (ou les deux) :  
  
- Consommer un autre composant  
  
- Être consommé par un autre composant  
  
  Par exemple, Imaginez une application d’achat qui possède un composant d’entrée de commande qui dépend des données de disponibilité du produit fournies par un composant d’inventaire de l’entrepôt. En termes MEF, la partie Inventory peut *Exporter* les données de disponibilité du produit, et la partie de l’entrée de commande peut *Importer* les données. La partie de l’entrée de commande et la partie inventaire n’ont pas besoin de connaître les unes des autres. le *conteneur de composition* (fourni par l’application hôte) est responsable de la gestion de l’ensemble des exportations et de la résolution des exportations et des importations.  
  
  Le conteneur de composition, <xref:System.ComponentModel.Composition.Hosting.CompositionContainer> , est généralement détenu par l’hôte. Le conteneur de composition conserve un *catalogue* des parties de composant exportées.  
  
### <a name="exporting-and-importing-component-parts"></a>Exportation et importation de composants  
 Vous pouvez exporter n’importe quelle fonctionnalité, à condition qu’elle soit implémentée en tant que classe publique ou membre public d’une classe (propriété ou méthode). Vous n’avez pas à dériver votre composant de composant à partir de <xref:System.ComponentModel.Composition.Primitives.ComposablePart> . Au lieu de cela, vous devez ajouter un <xref:System.ComponentModel.Composition.ExportAttribute> attribut à la classe ou au membre de classe que vous souhaitez exporter. Cet attribut spécifie le *contrat* par lequel une autre partie du composant peut importer vos fonctionnalités.  
  
### <a name="the-export-contract"></a>Le contrat d’exportation  
 <xref:System.ComponentModel.Composition.ExportAttribute>Définit l’entité (classe, interface ou structure) qui est exportée. En règle générale, l’attribut Export accepte un paramètre qui spécifie le type de l’exportation.  
  
```  
[Export(typeof(ContentTypeDefinition))]  
class TestContentTypeDefinition : ContentTypeDefinition {   }  
```  
  
 Par défaut, l' <xref:System.ComponentModel.Composition.ExportAttribute> attribut définit un contrat qui est le type de la classe d’exportation.  
  
```  
[Export]  
[Name("Structure")]  
[Order(After = "Selection", Before = "Text")]  
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }  
```  
  
 Dans l’exemple, l’attribut par défaut `[Export]` est équivalent à `[Export(typeof(TestAdornmentLayerDefinition))]` .  
  
 Vous pouvez également exporter une propriété ou une méthode, comme illustré dans l’exemple suivant.  
  
```  
[Export]  
[Name("Scarlet")]  
[Order(After = "Selection", Before = "Text")]  
public AdornmentLayerDefinition scarletLayerDefinition;  
```  
  
### <a name="importing-a-mef-export"></a>Importation d’une exportation MEF  
 Lorsque vous souhaitez utiliser une exportation MEF, vous devez connaître le contrat (généralement le type) par lequel il a été exporté et ajouter un <xref:System.ComponentModel.Composition.ImportAttribute> attribut qui a cette valeur. Par défaut, l’attribut import prend un paramètre, qui est le type de la classe qu’il modifie. Les lignes de code suivantes importent le <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> type.  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationRegistry;  
```  
  
## <a name="getting-editor-functionality-from-a-mef-component-part"></a>Obtention des fonctionnalités de l’éditeur à partir d’une partie du composant MEF  
 Si votre code existant est une partie du composant MEF, vous pouvez utiliser les métadonnées MEF pour consommer des composants de l’éditeur.  
  
#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Pour consommer les fonctionnalités de l’éditeur à partir d’une partie du composant MEF  
  
1. Ajoutez des références à System.Composition.ComponentModel.dll, qui se trouve dans le Global Assembly Cache (GAC) et aux assemblys de l’éditeur.  
  
2. Ajoutez les instructions using appropriées.  
  
    ```  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text;  
    ```  
  
3. Ajoutez l' `[Import]` attribut à votre interface de service, comme suit.  
  
    ```  
    [Import]  
    ITextBufferFactoryService textBufferService;  
    ```  
  
4. Une fois que vous avez obtenu le service, vous pouvez utiliser l’un de ses composants.  
  
5. Une fois que vous avez compilé votre assembly, placez-le dans le.. Dossier \Common7\IDE\Components\ de votre installation de Visual Studio.  
  
## <a name="see-also"></a>Voir aussi  
 [Points d’extension du service de langage et de l’éditeur](../extensibility/language-service-and-editor-extension-points.md)
