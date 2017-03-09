---
title: "Erreurs et avertissements de Modifier &amp; Continuer (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ENC2001"
  - "ENC1006"
  - "ENC2008"
  - "ENC1009"
  - "ENC1002"
  - "ENC2002"
  - "ENC1011"
  - "ENC1003"
  - "ENC1004"
  - "ENC1008"
  - "ENC1013"
  - "ENC2005"
  - "ENC1010"
  - "ENC2004"
  - "ENC1007"
  - "ENC1005"
  - "ENC2006"
  - "ENC1001"
  - "ENC2007"
  - "ENC2003"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Modifier & Continuer (C++), erreurs et avertissements"
  - "erreurs (C++), Modifier & Continuer"
  - "erreurs (débogueur), Modifier & Continuer"
ms.assetid: b5c5e25c-7ca4-4ca9-b91e-e8882de44dae
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "susanno"
manager: "douge"
---
# Erreurs et avertissements de Modifier &amp; Continuer (C++)
[!INCLUDE[cpp_current_short](../misc/includes/cpp_current_short_md.md)]Modifier & Continuer vous permet d'arrêter l'exécution d'un programme en mode Arrêt, d'apporter des modifications à l'exécution de code, puis de continuer l'exécution du programme avec les modifications récemment incorporées.  
  
 Les modifications de code déclaratif qui affectent la structure publique d'une classe sont interdites, et certaines modifications que vous pouvez apporter à une méthode, au corps d'une propriété ou à des déclarations privées dans une classe ne sont pas autorisées.  Autant que possible, Modifier & Continuer marque le code qui ne peut pas être modifié en gris clair et affiche un message d'erreur.  Pour plus d'informations sur les modifications non prises en charge par Modifier & Continuer pour [!INCLUDE[cpp_current_short](../misc/includes/cpp_current_short_md.md)], consultez [Modifier & Continuer \(Visual C\+\+\)](../debugger/edit-and-continue-visual-cpp.md).  
  
 Les erreurs et avertissements liés à Modifier & Continuer peuvent être résolus de l'une des façons suivantes :  
  
|Résolution|Nombre de messages d'erreur et d'avertissement|  
|----------------|----------------------------------------------------|  
|Arrêtez le débogage, réappliquez vos modifications, puis reprenez le débogage.|1001, 1002, 1003, 1004, 1005, 1006, 1007, 1008, 1010, 1013, 2003, 2005 Pour obtenir la liste des messages d'erreur et d'avertissement de cette catégorie, consultez [Redémarrage des messages de débogage](../misc/edit-and-continue-errors-and-warnings-cpp.md#BKMK_RestartDebuggingMessages).|  
|Dans le menu **Modifier**, choisissez **Annuler**, puis continuez à déboguer le code inchangé.<br /><br /> \- ou \-<br /><br /> Arrêtez le débogage, réappliquez vos modifications, puis reprenez le débogage.|1009, 1011 Pour obtenir la liste des messages d'erreur et d'avertissement de cette catégorie, consultez [Annuler ou arrêter des messages](../misc/edit-and-continue-errors-and-warnings-cpp.md#BKMK_UndoOrStopMessages).|  
|Poursuivez le débogage.  Vos modifications sont ignorées la première fois que le code est atteint, mais seront appliquées lors des appels suivants.|2001, 2002, 2004.  Pour obtenir la liste des messages d'erreur et d'avertissement de cette catégorie, consultez [Appliquer lors des messages d'appel suivants](../misc/edit-and-continue-errors-and-warnings-cpp.md#BKMK_ApplyAtNextCallMessages).|  
|Effectuez d'autres actions, telles que la redéfinition des points d'arrêt ou la régénération des modules avec la version actuelle de [!INCLUDE[cpp_current_short](../misc/includes/cpp_current_short_md.md)].|2007, 2008.  Pour obtenir la liste des messages d'erreur et d'avertissement de cette catégorie, consultez [Autres messages d'action requise](../misc/edit-and-continue-errors-and-warnings-cpp.md#BKMK_OtherActionRequiredMessages)|  
  
##  <a name="BKMK_RestartDebuggingMessages"></a> Redémarrage des messages de débogage  
 Les messages d'erreur suivants doivent être résolus en arrêtant la session de débogage en cours, en réappliquant les modifications que vous avez faites, puis en redémarrant la session de débogage.  
  
|||  
|-|-|  
|1001|Impossible de mettre à jour la conversion de code pour le symbole : *symbol* \(loc : *location*, conversion de code : *address*\)|  
|1002|Le symbole de données a changé \(*symbol*\)|  
|1003|Impossible de mapper la conversion de code pour la nouvelle fonction : *function*|  
|1004|Impossible d'ouvrir la base de données PDB pour la compression de type : *pdb* \(pdb\)|  
|1005|Le symbole a été renommé, supprimé ou modifié : *symbol*|  
|1006|Une variable globale ou statique a été ajoutée, renommée, supprimée ou modifiée au niveau de son type de données ou de son initialisation : *symbol* \(référencée par : *module*\)|  
|1007|Symbole non défini : *symbol* \(référencé par : *module*\)|  
|1008|Impossible d'effectuer l'initialisation d'exécution requise pour l'objet chargé durant la modification : *module*|  
|1010|Une variable statique ou globale a été ajoutée : *variable referenced in file*|  
|1013|Le débogueur a manqué d'espace mémoire lors de l'application des modifications du code|  
|2003|La modification de la position du code peut causer des erreurs de gestion des exceptions ou de destruction de variable : *function*|  
|2005|La nouvelle source fait partie du code.  Les informations de numéro de ligne du débogueur peuvent s'en ressentir : \(*function*\)|  
  
##  <a name="BKMK_UndoOrStopMessages"></a> Annuler ou arrêter des messages  
 Les messages d'erreur suivants peuvent être résolus en arrêtant la session de débogage en cours, en réappliquant les modifications que vous avez faites, puis en redémarrant la session de débogage.  
  
-   Dans le menu Edition, cliquez sur Annuler.  Vous pouvez continuer le débogage, mais les modifications ne sont pas appliquées.  
  
     \- ou \-  
  
-   Arrêtez le débogage, réappliquez les modifications, puis redémarrez le débogage.  
  
|||  
|-|-|  
|1009|Une variable statique ou globale a été supprimée : *variable referenced in file*|  
|1011|Une variable statique ou globale a été modifiée : *variable referenced in file*|  
  
##  <a name="BKMK_ApplyAtNextCallMessages"></a> Appliquer lors des messages d'appel suivants  
 Vous pouvez continuer votre session de débogage lorsque l'un des messages d'avertissement suivants s'affiche.  Vos modifications ne seront pas appliquées lors du premier appel du code après la modification ; les modifications seront appliquées dans tous les appels de code suivants.  
  
|||  
|-|-|  
|2001|Variable locale introuvable ou type de données de variable modifié : symbole \(*symbol*\)|  
|2002|Variable supprimée ou nouvelle variable locale requiert construction ou destruction : symbole \(*symbol*\)|  
|2004|Impossible de gérer l'ajout ou la suppression d'une variable locale dont le nom est déjà défini plus d'une fois : symbole \(*symbol*\)|  
  
##  <a name="BKMK_OtherActionRequiredMessages"></a> Autres messages d'action requise  
 L'action requise pour résoudre ces messages est décrite après le texte du message.  
  
|||  
|-|-|  
|2007|Impossible de déplacer certains points d'arrêt définis dans la fenêtre Code Machine.<br /><br /> Pour résoudre ce problème, réinitialisez les points d'arrêt affectés.|  
|2008|Impossible de charger les symboles de débogage du fichier *file* du module *module*.<br /><br /> Pour résoudre ce problème, régénérez le module spécifié avec la version actuelle de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].|  
  
## Voir aussi  
 [Modifier & Continuer \(Visual C\+\+\)](../debugger/edit-and-continue-visual-cpp.md)   
 [Modifier&Continuer](../debugger/edit-and-continue.md)