---
title: "Raccourcis clavier dans Workflow Designer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "WFDKeyboardShortcuts.UI"
ms.assetid: 9be75438-a4a3-4781-94e5-45b7ec082358
caps.latest.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# Raccourcis clavier dans Workflow Designer
Les fonctionnalités de base de [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] sont accessibles à partir du clavier.  
  
## Navigation dans Workflow Designer à l'aide du clavier  
 Dans [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)], les raccourcis globaux et les raccourcis de débogage s'appliquent à [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].Par ailleurs, plusieurs raccourcis clavier spécifiques à [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] ont été créés.Dans [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)], tous les raccourcis clavier peuvent être remappés.Toutefois, dans une application réhébergée, ces raccourcis clavier sont encodés de manière irréversible.  
  
### Raccourcis clavier de Workflow Designer  
 Le tableau suivant récapitule les raccourcis clavier par défaut affectés aux commandes de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Raccourci|Objectif|  
|---------------|--------------|  
|CTRL\+E, A|Affiche ou masque le concepteur d'arguments.|  
|CTRL\+E, C|Réduit l'activité sélectionnée sur place.|  
|CTRL\+E, E|Développe l'activité sélectionnée sur place.|  
|CTRL\+E, F|Connecte les activités sélectionnées dans un organigramme.|  
|CTRL\+E, I|Affiche ou masque le concepteur d'importations.|  
|CTRL\+E, M|Déplace le focus clavier vers l'élément suivant dans l'ordre de tabulation.|  
|CTRL\+E, N|Crée une variable dans la portée de l'activité sélectionnée \(ou la plus proche\).|  
|CTRL\+E, O|Affiche ou masque la vue d'ensemble.|  
|CTRL\+E, P|Accède au parent de l'activité sélectionnée.Cette commande permet de monter d'un niveau dans l'exploration à l'aide de la barre de navigation et et de modifier l'activité racine dans l'aire du concepteur.|  
|CTRL\+E, S|Ajoute l'élément avec le focus clavier à la sélection actuelle.|  
|CTRL\+E, V|Affiche ou masque le concepteur de variables.|  
|CTRL\+E, X|Développe toutes les activités dans le flux de travail.|  
|CTRL\+ALT\+F6|Déplace le focus clavier de la zone actuelle de l'interface utilisateur vers la zone suivante dans la séquence.L'ordre suivi est le suivant :<br /><br /> 1.  Barre d'exploration à l'aide de la barre de navigation<br />2.  Aire du concepteur<br />3.  Concepteur d'arguments\/de variables\/d'importations, s'il est ouvert<br />4.  Interpréteur de commandes|  
  
### Organigramme  
 La liste suivante affiche les mouvements utilisés pour construire un organigramme à l'aide du clavier.Comme dans le reste de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], les activités sont ajoutées à l'aire du concepteur à l'aide des raccourcis de boîte à outils globaux fournis avec [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)].  
  
-   Pour déplacer une activité, sélectionnez\-la et utilisez les touches de direction pour la repositionner.  
  
-   Pour redimensionner un organigramme, déplacez une activité au\-delà de la bordure actuelle de l'organigramme à l'aide des touches de direction.L'organigramme est redimensionné automatiquement.  
  
-   Pour définir une activité en tant que nœud Début, utilisez la commande **Définir en tant que StartNode** dans le menu contextuel.  
  
-   Pour connecter des activités :  
  
    1.  Sélectionnez l'activité source en y accédant par tabulation.  
  
    2.  Appuyez sur CTRL\+E, M autant de fois que nécessaire pour déplacer le focus clavier sur l'activité de destination.  
  
    3.  Appuyez sur CTRL\+E, S pour ajouter l'activité de destination à la sélection.  
  
    4.  Appuyez sur CTRL\+E, F pour ajouter le connecteur de la source à la destination.  
  
 Remarques à propos de la connexion des activités à l'aide du clavier :  
  
-   Vous pouvez établir plusieurs connexions en même temps en ajoutant d'autres activités à la sélection avant d'appuyer sur Ctrl\+E, F.Les connexions sont établies dans l'ordre dans lequel les activités ont été ajoutées à la sélection.  
  
-   Si une paire d'activités ne peut pas être connectée, par exemple si l'activité source possède déjà une connexion sortante, d'autres connexions entre les activités de la sélection sont établies dans la mesure du possible.  
  
-   Lorsque **FlowDecision** est inclus dans la sélection et que **FlowDecision** n'a pas de connecteurs sortants, le connecteur est placé sur la branche **True**.  
  
### Édition d'expressions  
 Par défaut, les raccourcis clavier par défaut pour l'édition de texte [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] s'appliquent dans l'éditeur d'expressions dans [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], avec les limitations suivantes :  
  
-   Le remappage des raccourcis clavier correspondant aux commandes suivantes n'a aucun effet.Vous pouvez utiliser uniquement les raccourcis clavier par défaut pour accéder aux commandes suivantes lors de la modification d'une expression.  
  
    1.  Couper  
  
    2.  Copier  
  
    3.  Coller  
  
    4.  Sélectionner tout  
  
    5.  Annuler  
  
    6.  Rétablir  
  
-   Pour remapper les raccourcis clavier des commandes d'édition d'expressions de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] dans [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)], modifiez les raccourcis au niveau de l'interface de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].Les modifications effectuées au niveau de l'interface de l'éditeur de texte ne s'appliquent pas automatiquement à [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].Si vous souhaitez remapper des raccourcis dans ces deux éléments, vous devez appliquer les modifications deux fois \(une fois pour chaque interface\).