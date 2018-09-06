---
title: Élément XML Ribbon
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VSTO.Ribbon.RibbonXMLItem
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, XML
- customizing the Ribbon, XML
- Ribbon [Office development in Visual Studio], XML
- callback methods
- custom Ribbon, displaying
- custom Ribbon, defining behavior
- XML [Office development in Visual Studio], Ribbon
- customizing the Ribbon, defining behavior
- Ribbon [Office development in Visual Studio], customizing
- customizing the Ribbon, displaying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e19e93423dc1437a41d4e15dd67fa669fb1cee5e
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35672845"
---
# <a name="ribbon-xml"></a>Élément XML Ribbon
  L’élément Ruban (XML) vous permet de personnaliser un ruban à l’aide de XML. Utilisez l’élément Ruban (XML) si vous souhaitez personnaliser le ruban d’une manière qui n’est pas pris en charge par l’élément Ruban (Concepteur visuel). Pour obtenir une comparaison de ce que vous pouvez faire avec chaque élément, consultez [vue d’ensemble du ruban](../vsto/Ribbon-overview.md).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
## <a name="add-a-ribbon-xml-item-to-a-project"></a>Ajouter un élément Ruban (XML) à un projet  
 Vous pouvez ajouter un élément **Ruban (XML)** à tout projet Office à partir de la boîte de dialogue **Ajouter un nouvel élément** . Visual Studio ajoute automatiquement les fichiers suivants à votre projet :  
  
-   Un fichier XML de ruban. Ce fichier définit l'interface utilisateur du ruban. Utilisez ce fichier pour ajouter des éléments d'interface utilisateur tels que des onglets, des groupes et des contrôles. Pour plus d’informations, consultez [référence du fichier XML de ruban](#RibbonDescriptorFile) plus loin dans cette rubrique.  
  
-   Un fichier de code du ruban. Ce fichier contient la *classe du ruban*. Cette classe porte le nom que vous avez spécifié pour l'élément **Ruban (XML)** dans la boîte de dialogue **Ajouter un nouvel élément** . Applications Microsoft Office utilisent une instance de cette classe pour charger le ruban personnalisé. Pour plus d’informations, consultez [référence de classe du ruban](#RibbonExtensionClass) plus loin dans cette rubrique.  
  
 Par défaut, ces fichiers ajoutent un groupe personnalisé pour le **Add-Ins** onglet du ruban.  
  
## <a name="display-the-custom-ribbon-in-a-microsoft-office-application"></a>Afficher le ruban personnalisé dans une application Microsoft Office  
 Après avoir ajouté un **ruban (XML)** élément à votre projet, vous devez ajouter le code pour le **ThisAddin**, **ThisWorkbook**, ou **ThisDocument** classe qui substitue le `CreateRibbonExtensibilityObject` méthode et retourne le code XML de ruban classe à l’application Office.  
  
 L'exemple de code suivant remplace la méthode `CreateRibbonExtensibilityObject` et retourne une classe XML de ruban nommée MyRibbon.  
  
 [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
 [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]  
  
## <a name="define-the-behavior-of-the-custom-ribbon"></a>Définir le comportement du ruban personnalisé  
 Vous pouvez répondre aux actions de l’utilisateur, telles qu’un clic sur un bouton du ruban, en créant *méthodes de rappel*. Les méthodes de rappel ressemblent aux événements figurant dans les contrôles Windows Forms, mais elles sont identifiées par un attribut dans le code XML de l'élément d'interface utilisateur. Vous écrivez des méthodes dans la classe du ruban et un contrôle appelle la méthode qui porte le même nom que la valeur d'attribut. Par exemple, vous pouvez créer une méthode de rappel qui est appelée lorsqu’un utilisateur clique sur un bouton sur le ruban. Deux étapes sont nécessaires pour créer une méthode de rappel :  
  
-   Assignez un attribut à un contrôle dans le fichier XML du ruban, qui identifie une méthode de rappel dans votre code.  
  
-   Définissez la méthode de rappel dans la classe du ruban.  
  
> [!NOTE]  
>  Outlook requiert une étape supplémentaire. Pour plus d’informations, consultez [personnaliser un ruban pour Outlook](../vsto/customizing-a-ribbon-for-outlook.md).  
  
 Pour une procédure pas à pas qui montre comment automatiser une application à partir du ruban, consultez [procédure pas à pas : créer un onglet personnalisé à l’aide du ruban XML](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md).  
  
### <a name="assign-callback-methods-to-controls"></a>Affecter des méthodes de rappel à des contrôles  
 Pour affecter une méthode de rappel à un contrôle dans le fichier XML du ruban, ajoutez un attribut qui spécifie le type et le nom de cette méthode. Par exemple, l'élément suivant définit un bouton doté d'une méthode de rappel **onAction** nommée `OnToggleButton1`.  
  
```xml  
<toggleButton id="toggleButton1" onAction="OnToggleButton1" />  
```  
  
 La méthode**onAction** est appelée quand l'utilisateur exécute la tâche principale associée à un contrôle particulier. Par exemple, la méthode de rappel **onAction** d'un bouton bascule est appelée quand l'utilisateur clique sur le bouton.  
  
 La méthode que vous spécifiez dans l'attribut peut avoir un nom quelconque. Toutefois, ce nom doit correspondre au nom de la méthode que vous définissez dans le fichier de code du ruban.  
  
 De nombreux types différents de méthodes de rappel peuvent être affectés aux contrôles du ruban. Pour obtenir une liste complète des méthodes de rappel disponibles pour chaque contrôle, consultez l’article technique [personnaliser l’interface utilisateur ruban d’Office (2007) pour les développeurs (partie 3 sur 3)](http://msdn.microsoft.com/a16c7df5-93f3-4920-baa8-7b7290794c15).  
  
###  <a name="CallBackMethods"></a> Définir des méthodes de rappel  
 Définissez vos méthodes de rappel dans la classe du ruban, dans le fichier de code du ruban. Une méthode de rappel a plusieurs conditions requises :  
  
-   Elle doit être déclarée comme publique.  
  
-   Son nom doit correspondre au nom d'une méthode de rappel que vous avez affectée à un contrôle dans le fichier XML du ruban.  
  
-   Sa signature doit correspondre à la signature d'un type de méthode de rappel disponible pour le contrôle du ruban associé.  
  
 Pour obtenir une liste complète des signatures de méthode de rappel pour les contrôles de ruban, consultez l’article technique [personnaliser l’interface utilisateur ruban d’Office (2007) pour les développeurs (partie 3 sur 3)](http://msdn.microsoft.com/a16c7df5-93f3-4920-baa8-7b7290794c15). Visual Studio ne fournit pas de prise en charge IntelliSense pour les méthodes de rappel que vous créez dans le fichier de code du ruban. Si vous créez une méthode de rappel qui ne correspond pas à une signature valide, le code est compilé mais rien ne se passe quand l'utilisateur clique sur le contrôle.  
  
 Toutes les méthodes de rappel ont un paramètre <xref:Microsoft.Office.Core.IRibbonControl> qui représente le contrôle qui a appelé la méthode. Ce paramètre permet de réutiliser la même méthode de rappel pour plusieurs contrôles. L'exemple de code suivant présente une méthode de rappel **onAction** qui exécute différentes tâches en fonction du contrôle sur lequel l'utilisateur clique.  
  
 [!code-csharp[Trin_RibbonOutlookBasic#2](../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs#2)]
 [!code-vb[Trin_RibbonOutlookBasic#2](../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb#2)]  
  
##  <a name="RibbonDescriptorFile"></a> Référence de fichier XML du ruban  
 Vous pouvez définir votre ruban personnalisé en ajoutant des éléments et attributs dans le fichier XML du ruban. Par défaut, le fichier XML du ruban contient le code XML suivant.  
  
```xml  
<?xml version="1.0" encoding="UTF-8"?>  
<customUI xmlns="http://schemas.microsoft.com/office/2006/01/customui" onLoad="OnLoad">  
  <ribbon>  
    <tabs>  
      <tab idMso="TabAddIns">  
        <group id="MyGroup"  
               label="My Group">  
        </group>  
      </tab>  
    </tabs>  
  </ribbon>  
</customUI>  
```  
  
 Le tableau suivant décrit les éléments par défaut du fichier XML du ruban.  
  
|Élément|Description|  
|-------------|-----------------|  
|**customUI**|Représente le ruban personnalisé dans le projet de complément VSTO.|  
|**ribbon**|Représente le ruban.|  
|**Onglets**|Représente un ensemble d'onglets du ruban.|  
|**Onglet**|Représente un onglet individuel du ruban.|  
|**group**|Représente un groupe de contrôles sous l'onglet du ruban.|  
  
 Ces éléments ont des attributs qui spécifient l’apparence et le comportement du ruban personnalisé. Le tableau suivant décrit les attributs par défaut figurant dans le fichier XML du ruban.  
  
|Attribut|Élément parent|Description|  
|---------------|--------------------|-----------------|  
|**onLoad**|**customUI**|Identifie une méthode qui est appelée lorsque l’application charge le ruban.|  
|**idMso**|**Onglet**|Identifie un onglet intégré à afficher dans le ruban.|  
|**ID**|**group**|Identifie le groupe.|  
|**Étiquette**|**group**|Spécifie le texte qui apparaît sur le groupe.|  
  
 Les éléments et les attributs par défaut figurant dans le fichier XML du ruban sont un petit sous-ensemble des éléments et attributs disponibles. Pour obtenir une liste complète des éléments disponibles et des attributs, consultez l’article technique [personnaliser l’interface utilisateur ruban d’Office (2007) pour les développeurs (partie 2 sur 3)](http://msdn.microsoft.com/6b904f55-525f-4520-9b81-a017db65657b).  
  
##  <a name="RibbonExtensionClass"></a> Référence de classe du ruban  
 Visual Studio génère la classe du ruban dans le fichier de code du ruban. Ajoutez les méthodes de rappel pour les contrôles sur le ruban à cette classe. Cette classe implémente l'interface <xref:Microsoft.Office.Core.IRibbonExtensibility> .  
  
 Le tableau suivant décrit les méthodes par défaut de cette classe.  
  
|Méthode|Description|  
|------------|-----------------|  
|`GetCustomUI`|Retourne le contenu du fichier XML du ruban. Applications Microsoft Office appellent cette méthode pour obtenir une chaîne XML qui définit l’interface utilisateur de votre ruban personnalisé. Cette méthode implémente la méthode <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> . **Remarque :** `GetCustomUI` doit être implémentée uniquement pour retourner le contenu du fichier XML du ruban ; elle ne doit pas être utilisée pour initialiser votre complément, VSTO.   En particulier, vous ne devez pas essayer d'afficher des boîtes de dialogue ni d'autres fenêtres dans votre implémentation de `GetCustomUI` . Sinon, le ruban personnalisé ne peut pas fonctionner correctement. Si vous devez exécuter du code qui initialise votre complément VSTO, ajoutez ce code au gestionnaire d’événements `ThisAddIn_Startup` .|  
|`OnLoad`|Affecte le paramètre <xref:Microsoft.Office.Core.IRibbonControl>au champ `Ribbon`. Applications Microsoft Office appellent cette méthode quand elles chargent le ruban personnalisé. Vous pouvez utiliser ce champ à mettre à jour dynamiquement le ruban personnalisé. Pour plus d’informations, consultez l’article technique [personnaliser l’interface utilisateur ruban d’Office (2007) pour les développeurs (partie 1 sur 3)](http://msdn.microsoft.com/a4fd6d18-d4a8-4e64-bd89-f437208573d3).|  
|`GetResourceText`|Appelée par la méthode `GetCustomUI` pour obtenir le contenu du fichier XML du ruban.|  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du ruban](../vsto/ribbon-overview.md)   
 [Procédure pas à pas : Créer un onglet personnalisé à l’aide de XML du ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)   
 [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md)  
  
  