---
title: "Param&#232;tres avanc&#233;s du compilateur, bo&#238;te de dialogue (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesAdvancedCompile"
helpviewer_keywords: 
  - "Boîte de dialogue Paramètres avancés du compilateur"
ms.assetid: 1f81133a-293f-4dba-bc1c-8baafb01d857
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# Param&#232;tres avanc&#233;s du compilateur, bo&#238;te de dialogue (Visual Basic)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Utilisez la boîte de dialogue **Paramètres avancés du compilateur** du **Concepteur de projets** pour spécifier les propriétés de configuration de build avancées du projet.  Cette boîte de dialogue s'applique uniquement aux projets Visual Basic.  
  
### Pour accéder à cette boîte de dialogue  
  
1.  Dans **Explorateur de solutions**, sélectionnez un nœud de projet \(pas le nœud **Solution** \).  
  
2.  Dans le menu **Projet**, cliquez sur **Propriétés**.  Lorsque le **Concepteur de projets** apparaît, cliquez sur l'onglet **Compiler**.  
  
3.  Dans [Page Compiler, Concepteur de projets \(Visual Basic\)](../../ide/reference/compile-page-project-designer-visual-basic.md), sélectionnez **Configuration** et **Plateforme**.  Dans les configurations de build simplifiées, les listes **Configuration** et **Plateforme** ne sont pas affichées.  Pour plus d'informations, consultez [Debug and Release Project Configurations](http://msdn.microsoft.com/fr-fr/0440b300-0614-4511-901a-105b771b236e).  
  
4.  Cliquez sur **Options avancées de compilation**.  
  
 [!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]  
  
## Optimisations  
 Les options suivantes spécifient les optimisations qui peuvent, dans certains cas, réduire la taille d'un fichier programme, rendre l'exécution d'une application plus rapide ou accélérer le processus de génération.  
  
 **Supprimer les contrôles de dépassement sur les entiers**  
 Par défaut, cette case à cocher est désactivée pour activer la vérification de dépassement sur les entiers.  Activez cette case à cocher pour supprimer le contrôle de dépassement sur les entiers.  Si vous activez cette case à cocher, les calculs entiers peuvent être plus rapides.  Toutefois, si vous supprimez le contrôle de dépassement de capacité et des fonctions de type de données, dépassement de capacité des résultats incorrects peuvent être stockés sans erreur est déclenchée.  
  
 Si des rapports de dépassement de capacité sont archivés et les dépassements de capacité d'une opération d'entier, une exception d' <xref:System.OverflowException> est levée.  Si des rapports de dépassement de capacité ne sont pas contrôlés, les dépassements de capacité entiers d'exécution ne lèvent pas d'exception.  
  
 **Activer les optimisations**  
 Cette case à cocher est désactivée par défaut pour désactiver les optimisations du compilateur.  Activez cette case à cocher pour activer les optimisations du compilateur.  Les optimisations du compilateur diminuent la taille du fichier de sortie, le rendent plus rapide et plus efficace.  Toutefois, comme les optimisations entraînent la réorganisation de code dans le fichier de sortie, les optimisations du compilateur peuvent rendre le débogage difficile.  
  
 **Adresse de base de la DLL**  
 Cette zone de texte affiche l'adresse de base par défaut de la DLL au format hexadécimal.  Dans les projets Bibliothèque de contrôle et Bibliothèque de classe, vous pouvez utiliser cette zone de texte pour spécifier l'adresse de base à utiliser lors de la création de la DLL.  
  
 **Générer des informations de débogage**  
 Dans la liste, sélectionnez **Aucun**, **Complet** ou **pdb\-only**.  **Aucun** spécifie qu'aucune information de débogage n'est générée.  **Complet** spécifie que les informations complètes de débogage sont générées et **pdb\-only** spécifie que seules les informations de débogage PDB sont générées.  Par défaut, cette option a la valeur **Complet**.  
  
## Constantes de compilation  
 Les constantes de compilation conditionnelle ont un effet similaire à celui à utiliser une directive de préprocesseur d' [\#Const](/dotnet/visual-basic/language-reference/directives/const-directive) dans un fichier source, mais les constantes sont publiques et s'appliquent à tous les fichiers du projet.  Vous pouvez utiliser des constantes de compilation conditionnelle avec la directive d' [\#Else \#If… Then…](/dotnet/visual-basic/language-reference/directives/if-then-else-directives) pour compiler des fichiers sources conditionnelle.  Consultez [Conditional Compilation](/dotnet/visual-basic/programming-guide/program-structure/conditional-compilation).  
  
 **Définir la constante DEBUG**  
 Par défaut, cette case à cocher est activée, spécifiant qu'une constante DEBUG est définie.  
  
 **Définir la constante TRACE**  
 Par défaut, cette case à cocher est activée, spécifiant qu'une constante TRACE est définie.  
  
 **Constantes personnalisées**  
 Entrez les constantes personnalisées pour votre application dans cette zone de texte.  Les entrées doivent être délimitées par une virgule selon le format suivant : Nom1 \= "Valeur1", Nom2 \= "Valeur2", Nom3 \= "Valeur3."  
  
## D'autres paramètres  
 **Générer des assemblys de sérialisation**  
 Ce paramètre spécifie si le compilateur utilise l' pour créer des assemblys de sérialisation XML.  Les assemblys de sérialisation peuvent améliorer les performances de démarrage de <xref:System.Xml.Serialization.XmlSerializer> si vous avez utilisé cette classe pour sérialiser les types dans votre code.  Par défaut, cette option a la valeur **Auto**, qui spécifie que les assemblys de sérialisation ne peuvent être générés que si vous avez utilisé <xref:System.Xml.Serialization.XmlSerializer> pour encoder les types dans votre code en XML.  **Inactif** spécifie que ces assemblys de sérialisation ne doivent jamais être générés, indépendamment du fait que votre code utilise ou pas <xref:System.Xml.Serialization.XmlSerializer>.  **Actif** spécifie que les assemblys de sérialisation doivent toujours être générés.  Les assemblys de sérialisation sont appelés `TypeName`.XmlSerializers .dll.  
  
## Voir aussi  
 [Page Compiler, Concepteur de projets \(Visual Basic\)](../../ide/reference/compile-page-project-designer-visual-basic.md)