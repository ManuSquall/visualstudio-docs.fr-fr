---
title: "&#201;diteur d&#39;ensemble de r&#232;gles, bo&#238;te de dialogue (h&#233;rit&#233;e) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Workflow.Activities.Rules.Design.RuleSetDialog.UI"
helpviewer_keywords: 
  - "Éditeur d'ensemble de règles (boîte de dialogue)"
ms.assetid: 7cfd5df1-1115-4e5c-9b72-121f39419e83
caps.latest.revision: 7
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# &#201;diteur d&#39;ensemble de r&#232;gles, bo&#238;te de dialogue (h&#233;rit&#233;e)
Cette rubrique explique comment utiliser la boîte de dialogue **Éditeur d'ensembles de règles** dans le [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] hérité.Utilisez le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 La boîte de dialogue **Éditeur d'ensemble de règles** permet de créer et de modifier des ensembles de règles [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) sérialisés dans un fichier de règles.  
  
> [!NOTE]
>  Si vous souhaitez ouvrir le fichier .rules avec l'**Éditeur XML avec encodage**, vous devez au préalable fermer la fenêtre du concepteur correspondante pour le workflow ou l'activité concerné\(e\).  
  
 Pour plus d'informations sur l'accès à la boîte de dialogue **Éditeur d'ensemble de règles**, consultez [Procédure : créer un ensemble de règles PolicyActivity \(héritée\)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md).  
  
> [!WARNING]
>  L'éditeur de règles du [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] hérité utilisé pour cibler le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] ne prend pas en charge le multi\-ciblage.  
  
 Le tableau suivant décrit les éléments d'interface utilisateur de la boîte de dialogue **Éditeur d'ensemble de règles**.  
  
|Élément d'interface|Description|  
|-------------------------|-----------------|  
|**Ajouter une règle**|Ajoute une nouvelle définition de règle à l'ensemble de règles.|  
|**Supprimer**|Supprime la règle sélectionnée de l'ensemble de règles.|  
|**Chaînage**|Spécifie le type de chaînage avant à utiliser avec l'ensemble de règles.Les options disponibles sont les suivantes :<br /><br /> -   **Chaînage complet**, qui spécifie l'utilisation de tous les mécanismes de chaînage avant : implicite, attribution de méthode et explicite avec fonction **Update**.<br />-   **Séquentiel**, qui spécifie de ne pas utiliser de chaînage avant.<br />-   **Mise à jour explicite uniquement**, qui spécifie d'exécuter uniquement le chaînage avant sur les actions de **mise à jour**.<br /><br /> Pour plus d'informations sur le chaînage avant, consultez [Utilisation de l'activité PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004) \(page pouvant être en anglais\).|  
|**Nom**|En\-tête de colonne de la liste des ensembles de règles.Cliquez pour trier la liste de règles par nom.|  
|**Priorité**|En\-tête de colonne de la liste des ensembles de règles.Cliquez pour trier la liste de règles par priorité.|  
|**Réévaluation**|En\-tête de colonne de la liste des ensembles de règles.Cliquez pour trier la liste de règles par type de réévaluation.|  
|**Aperçu de la règle**|En\-tête de colonne de la liste des ensembles de règles.Cliquez pour trier la liste de règles par l'aperçu de la condition d'une règle et actions.|  
|**Nom:**|Entrez le nom de la règle.|  
|**Priorité :**|Entrez une priorité pour la règle.La priorité par défaut est 0.|  
|**Réévaluation :**|Spécifie le type de réévaluation de règle à utiliser avec la règle.Les options disponibles sont les suivantes :<br /><br /> -   **Toujours**, qui entraîne la réévaluation de la règle, en cas de besoin.<br />-   **Jamais**, qui spécifie que la règle ne doit jamais être réévaluée.Dans ce cas, la règle est exécutée une seule fois.|  
|**Active**|Cochez pour rendre la règle active.|  
|**Condition :**|Entrez une expression pour la condition de règle.Pour plus d'informations sur la syntaxe d'expression, consultez la section consacrée à l'entrée de conditions et d'expressions d'actions dans cette page.|  
|**Actions THEN :**|Entrez une expression applicable aux actions THEN.Pour plus d'informations sur la syntaxe d'expression, consultez la section consacrée à l'entrée de conditions et d'expressions d'actions dans cette page.|  
|**Actions ELSE :**|Entrez une expression applicable aux actions ELSE.Pour plus d'informations sur la syntaxe d'expression, consultez la section consacrée à l'entrée de conditions et d'expressions d'actions dans cette page.|  
|**OK**|Cliquez pour enregistrer l'ensemble de règles dans un fichier .rules.|  
  
 Pour plus d'informations sur les ensembles de règles, consultez [Utilisation de l'activité PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004) \(page pouvant être en anglais\).  
  
## Entrée de conditions et d'expressions d'actions  
 Vous entrez des expressions pour les conditions et pour les actions THEN et ELSE sous forme de texte dans leurs zones de texte respectives, dans la boîte de dialogue **Éditeur d'ensemble de règles**.Vous pouvez taper **this.** dans l'éditeur pour référencer des champs, des propriétés et des méthodes utilisés dans le workflow, à l'aide d'un type\-de menu IntelliSense.Vous pouvez également taper directement un nom de membre de workflow.Vous pouvez appeler des méthodes statiques appartenant aux types référencés ; pour cela, tapez le nom de la classe suivi du nom de la méthode.  
  
 Vous pouvez ajouter des opérateurs logiques à la condition, tels que les opérateurs AND, OR ou NOT.Vous pouvez également ajouter des prédicats.Un prédicat se compose d'un opérateur binaire et de deux opérandes.Les opérateurs binaires pris en charge sont les suivants : \=\=, \>, \<, \>\= et \<\=.Les opérandes pris en charge sont à valeur de constante, à fonction arithmétique et à portée publique.  
  
 Vous pouvez spécifier le type de comparaison et comparer à la valeur **null** ou à une chaîne vide.Vous pouvez imbriquer des appels à des membres sur une variable qui contient un type complexe, par exemple `this.Address.State == "WA"`.  
  
 Les expressions prennent en charge les opérateurs suivants :  
  
-   Opérateurs relationnels: \=\=, \=, \!\=  
  
-   Opérateurs de comparaison : \<, \<\=, \>, \>\=  
  
-   Opérateurs arithmétiques: \+, \- , \*, \/, MOD  
  
-   Opérateurs logiques : AND, &&, OR, &#124;&#124;, NOT, \!  
  
-   Opérateurs de bits : &, &#124;  
  
 La priorité des opérateurs d'expression suit les règles de priorité des opérateurs C\#.  
  
 Pour plus d'informations sur les conditions, consultez [Using Conditions in Workflows](http://msdn.microsoft.com/fr-fr/541211f5-d382-4810-894f-71f00b34fa77).  
  
### Fonctions d'arrêt et de mise à jour  
 Les expressions **Actions THEN** et **Actions ELSE** prennent en charge les fonctions **Halt** et **Update**.Pour utiliser la fonction **Halt**, tapez **Halt** dans une zone de texte **Action THEN** ou **Action ELSE**.L'action **Halt** provoque l'arrêt immédiat de l'exécution de l'ensemble de règles, ainsi que le retour du contrôle au code appelant.La fonction **Update** s'utilise avec le chaînage avant.  
  
 Une instruction **Update** peut être exprimée dans l'éditeur, dans l'un de deux formulaires ; ces deux formulaires sont illustrés dans l'exemple suivant :  
  
```  
Update(this.Address.State)  
Update("this/Address/State")  
```  
  
 Pour plus d'informations sur l'utilisation de l'instruction **Update** avec le chaînage avant, consultez [Utilisation de l'activité PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004) \(page pouvant être en anglais\).  
  
## Voir aussi  
 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)   
 [Sélectionner l'ensemble de règles, boîte de dialogue \(héritée\)](../workflow-designer/select-rule-set-dialog-box-legacy.md)   
 [Utilisation de l'activité PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004)   
 [Utilisation de conditions dans les workflows](http://go.microsoft.com/fwlink?LinkID=65009)