---
title: Éditeur d’ensemble de règles, boîte de dialogue (héritée) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleSetDialog.UI
helpviewer_keywords:
- Rule Set Editor dialog box
ms.assetid: 7cfd5df1-1115-4e5c-9b72-121f39419e83
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8010bbbc38dee980ebe89dc60ccb513379103a26
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75846312"
---
# <a name="rule-set-editor-dialog-box-legacy"></a>Éditeur d'ensemble de règles, boîte de dialogue (héritée)
Cette rubrique décrit comment utiliser la boîte de dialogue **éditeur d’ensemble de règles** dans le hérité [!INCLUDE[wfd1](../includes/wfd1-md.md)] . Utilisez le [!INCLUDE[wfd2](../includes/wfd2-md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 La boîte de dialogue **éditeur d’ensemble de règles** permet de créer et de modifier des ensembles de règles [PolicyActivity](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx) , qui sont sérialisés dans un fichier. Rules.

> [!NOTE]
> Si vous souhaitez ouvrir le fichier. Rules avec l' **éditeur XML avec encodage**, vous devez d’abord fermer la fenêtre du concepteur associée pour le flux de travail ou l’activité.

 Pour plus d’informations sur l’accès à la boîte de dialogue **éditeur d’ensemble de règles** , consultez [procédure : créer un ensemble de règles PolicyActivity (hérité)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md).

> [!WARNING]
> L'éditeur de règles du [!INCLUDE[wfd2](../includes/wfd2-md.md)] hérité utilisé pour cibler le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] ne prend pas en charge le multi-ciblage.

 Le tableau suivant décrit les éléments d’interface utilisateur de la boîte de dialogue **éditeur d’ensemble de règles** .

|Élément de l’interface utilisateur|Description|
|----------------|-----------------|
|**Ajouter une règle**|Ajoute une nouvelle définition de règle à l'ensemble de règles.|
|**Supprimer**|Supprime la règle sélectionnée de l'ensemble de règles.|
|**Chaînage**|Spécifie le type de chaînage avant à utiliser avec l'ensemble de règles. Options disponibles :<br /><br /> -   **Chaînage complet**, qui spécifie d’utiliser tous les mécanismes de chaînage avant : implicite, attribution de méthode et Explicit à l’aide d’une fonction de **mise à jour** .<br />-   **Séquentiel**, qui spécifie de ne pas utiliser de chaînage avant.<br />-   **Mise à jour explicite uniquement**, qui spécifie d’exécuter uniquement le chaînage avant sur les actions de **mise à jour** .<br /><br /> Pour plus d’informations sur le chaînage avant, consultez [utilisation de l’activité PolicyActivity](https://msdn2.microsoft.com/library/bb675229.aspx).|
|**Nom**|En-tête de colonne de la liste des ensembles de règles. Cliquez pour trier la liste de règles par nom.|
|**Priorité**|En-tête de colonne de la liste des ensembles de règles. Cliquez pour trier la liste de règles par priorité.|
|**Réévaluation**|En-tête de colonne de la liste des ensembles de règles. Cliquez pour trier la liste de règles par type de réévaluation.|
|**Aperçu de la règle**|En-tête de colonne de la liste des ensembles de règles. Cliquez pour trier la liste de règles par l'aperçu de la condition d'une règle et actions.|
|**Nom :**|Entrez le nom de la règle.|
|**Importance**|Entrez une priorité pour la règle. La priorité par défaut est 0.|
|**Réévaluation :**|Spécifie le type de réévaluation de règle à utiliser avec la règle. Options disponibles :<br /><br /> -   **Toujours**, ce qui entraîne la réévaluation de la règle en fonction des besoins.<br />-   **Jamais**, ce qui entraîne la réévaluation de la règle. Dans ce cas, la règle est exécutée une seule fois.|
|**Actif**|Cochez pour rendre la règle active.|
|**Etat**|Entrez une expression pour la condition de règle. Pour plus d'informations sur la syntaxe d'expression, consultez la section consacrée à l'entrée de conditions et d'expressions d'actions dans cette page.|
|**Actions THEN :**|Entrez une expression applicable aux actions THEN. Pour plus d'informations sur la syntaxe d'expression, consultez la section consacrée à l'entrée de conditions et d'expressions d'actions dans cette page.|
|**Actions ELSE :**|Entrez une expression applicable aux actions ELSE. Pour plus d'informations sur la syntaxe d'expression, consultez la section consacrée à l'entrée de conditions et d'expressions d'actions dans cette page.|
|**OK**|Cliquez pour enregistrer l'ensemble de règles dans un fichier .rules.|

 Pour plus d’informations sur les ensembles de règles, consultez [utilisation de l’activité PolicyActivity](https://msdn2.microsoft.com/library/bb675229.aspx).

## <a name="entering-condition-and-action-expressions"></a>Entrée de conditions et d'expressions d'actions
 Vous entrez des expressions pour la condition et les actions Then et Else sous forme de texte dans leurs zones de texte respectives dans la boîte de dialogue **éditeur d’ensemble de règles** . Vous pouvez taper **cette.** dans l’éditeur pour référencer les champs, les propriétés et les méthodes utilisés dans le workflow, à l’aide d’un type de menu IntelliSense. Vous pouvez également taper directement un nom de membre de workflow. Vous pouvez appeler des méthodes statiques appartenant aux types référencés ; pour cela, tapez le nom de la classe suivi du nom de la méthode.

 Vous pouvez ajouter des opérateurs logiques à la condition, tels que les opérateurs AND, OR ou NOT. Vous pouvez également ajouter des prédicats. Un prédicat se compose d’un opérateur binaire et de deux opérandes. Les opérateurs binaires pris en charge sont = =, >, \<, > = et <=. Les opérandes pris en charge sont à valeur de constante, à fonction arithmétique et à portée publique.

 Vous pouvez spécifier le type de comparaison, et vous pouvez comparer à une **valeur null** ou à une chaîne vide. Vous pouvez imbriquer des appels à des membres sur une variable qui contient un type complexe, par exemple `this.Address.State == "WA"`.

 Les expressions prennent en charge les opérateurs suivants :

- Opérateurs relationnels: ==, =, !=

- Opérateurs de comparaison : <, \<=, > , >=

- Opérateurs arithmétiques: +, - , *, /, MOD

- Opérateurs logiques : AND,  && ou,  &#124;&#124;, NOT, !

- Opérateurs au niveau du bit : &, &#124;

  La priorité des opérateurs d'expression suit les règles de priorité des opérateurs C#.

  Pour plus d’informations sur les conditions, consultez [utilisation de conditions dans les workflows](https://msdn.microsoft.com/541211f5-d382-4810-894f-71f00b34fa77).

### <a name="halt-and-update-functions"></a>Fonctions d'arrêt et de mise à jour
 **Then actions :** et **else actions :** les expressions prennent en charge les fonctions d' **arrêt** et de **mise à jour** . Pour utiliser la fonction **Halt** , tapez **Halt** dans une zone de texte **action Then :** ou **autre action :** . L’action d' **arrêt** provoque l’arrêt immédiat de l’exécution de l’ensemble de règles, et le contrôle retourne au code appelant. Vous utilisez la fonction de **mise à jour** avec le chaînage avant.

 Une instruction **Update** peut être exprimée dans l’éditeur sous l’une des deux formes suivantes : les deux formes sont présentées dans l’exemple suivant :

```
Update(this.Address.State)
Update("this/Address/State")
```

 Pour plus d’informations sur l’utilisation de la **mise à jour** avec le chaînage avant, consultez [utilisation de l’activité PolicyActivity](https://msdn2.microsoft.com/library/bb675229.aspx).

## <a name="see-also"></a>Voir aussi
 [PolicyActivity](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx) [Sélectionner l’ensemble de règles, boîte de dialogue (héritée)](../workflow-designer/select-rule-set-dialog-box-legacy.md) [à l’aide de l’activité PolicyActivity](https://msdn2.microsoft.com/library/bb675229.aspx) [à l’aide de conditions dans les workflows](https://msdn2.microsoft.com/library/bb628447.aspx)
