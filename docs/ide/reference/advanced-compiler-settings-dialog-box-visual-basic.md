---
title: "Paramètres avancés du compilateur, boîte de dialogue (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vb.ProjectPropertiesAdvancedCompile
helpviewer_keywords:
- Advanced Compiler Settings dialog box
ms.assetid: 1f81133a-293f-4dba-bc1c-8baafb01d857
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b2e8661fb7984fd5b04b64211bf209827683ee0a
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2018
---
# <a name="advanced-compiler-settings-dialog-box-visual-basic"></a>Paramètres avancés du compilateur, boîte de dialogue (Visual Basic)

Utilisez la boîte de dialogue **Paramètres avancés du compilateur** du **Concepteur de projets** pour spécifier les propriétés de configuration de build avancées du projet. Cette boîte de dialogue s’applique uniquement aux projets Visual Basic.  
  
### <a name="to-access-this-dialog-box"></a>Pour accéder à cette boîte de dialogue
  
1.  Dans l’**Explorateur de solutions**, choisissez un nœud de projet (pas le nœud **Solution**).  
  
2.  Dans le menu **Projet**, cliquez sur **Propriétés**. Quand le **Concepteur de projets** apparaît, cliquez sur l’onglet **Compiler**.  
  
3.  Dans la [page Compiler, Concepteur de projets (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md), sélectionnez **Configuration** et **Plateforme**. Dans les configurations de build simplifiées, les listes **Configuration** et **Plateforme**  ne sont pas affichées. Pour plus d’informations, consultez [Guide pratique pour définir des configurations Debug et Release](../../debugger/how-to-set-debug-and-release-configurations.md).
  
4.  Cliquez sur **Options avancées de compilation**.  
  
 [!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="optimizations"></a>Optimisations  
 Les options suivantes spécifient les optimisations qui peuvent, dans certains cas, réduire la taille d’un fichier programme, rendre l’exécution d’un programme plus rapide ou accélérer le processus de génération.  
  
 **Supprimer les contrôles de dépassement sur les entiers**  
 Par défaut, cette case est décochée pour activer la vérification de dépassement sur les entiers. Cochez cette case pour supprimer la vérification de dépassement sur les entiers. Si vous cochez cette case, les calculs d’entiers peuvent être plus rapides. Toutefois, si vous supprimez la vérification de dépassement et le dépassement de capacité de type de données, des résultats incorrects peuvent être stockés sans déclencher d’erreur.  
  
 Si les conditions de dépassement sont vérifiées et qu’une opération entière génère un dépassement de capacité, une exception <xref:System.OverflowException> est levée. Si les conditions de dépassement ne sont pas vérifiées, les dépassements de capacité d’une opération entière ne lèvent pas d’exception.  
  
 **Activer les optimisations**  
 Par défaut, cette case est décochée pour désactiver les optimisations du compilateur. Cochez cette case pour activer les optimisations du compilateur. Les optimisations du compilateur diminuent la taille du fichier de sortie, le rendent plus rapide et plus efficace. Toutefois, comme les optimisations entraînent la réorganisation de code dans le fichier de sortie, les optimisations du compilateur peuvent rendre le débogage difficile.  
  
 **Adresse de base de la DLL**  
 Cette zone de texte affiche l’adresse de base de la DLL par défaut au format hexadécimal. Dans les projets de bibliothèque de contrôle et de bibliothèque de classes, vous pouvez utiliser cette zone de texte pour spécifier l’adresse de base à utiliser lors de la création de la DLL.  
  
 **Générer des infos de débogage**  
 Sélectionnez **Aucun**, **Complet**  ou **pdb-only** dans la liste. **Aucun** spécifie qu’aucune information de débogage n’est générée. **Complet** spécifie que les informations complètes de débogage sont générées et **pdb-only** spécifie que seules les informations de débogage PDB sont générées. Par défaut, cette option a la valeur **Complet**.  
  
## <a name="compilation-constants"></a>Constantes de compilation  
 Les constantes de compilation conditionnelle reviennent à utiliser une directive de préprocesseur [#Const](/dotnet/visual-basic/language-reference/directives/const-directive) dans un fichier source, sauf que les constantes définies sont publiques et s’appliquent à tous les fichiers du projet. Vous pouvez utiliser des constantes de compilation conditionnelle avec la directive [#If...Then...#Else](/dotnet/visual-basic/language-reference/directives/if-then-else-directives) pour compiler des fichiers sources de façon conditionnelle. Consultez [Compilation conditionnelle](/dotnet/visual-basic/programming-guide/program-structure/conditional-compilation).  
  
 **Définir la constante DEBUG**  
 Par défaut, cette case est cochée, spécifiant qu’une constante DEBUG est définie.  
  
 **Définir la constante TRACE**  
 Par défaut, cette case est cochée, spécifiant qu’une constante TRACE est définie.  
  
 **Constantes personnalisées**  
 Entrez les constantes personnalisées pour votre application dans cette zone de texte. Les entrées doivent être délimitées par une virgule selon le format suivant : **Nom1="Valeur1",Nom2="Valeur2",Nom3="Valeur3"**.  
  
## <a name="other-settings"></a>Autres paramètres

 **Générer des assemblys de sérialisation**  
 Ce paramètre spécifie si le compilateur crée des assemblys de sérialisation XML. Les assemblys de sérialisation peuvent améliorer les performances de démarrage de <xref:System.Xml.Serialization.XmlSerializer> si vous avez utilisé cette classe pour sérialiser les types dans votre code. Par défaut, cette option a la valeur **Auto**, qui spécifie que les assemblys de sérialisation ne peuvent être générés que si vous avez utilisé <xref:System.Xml.Serialization.XmlSerializer> pour encoder les types dans votre code en XML. **Inactif** spécifie que les assemblys de sérialisation ne doivent jamais être générés, que votre code utilise <xref:System.Xml.Serialization.XmlSerializer> ou non. **Actif** spécifie que les assemblys de sérialisation doivent toujours être générés. Les assemblys de sérialisation sont appelés `TypeName`.XmlSerializers.dll.  

## <a name="see-also"></a>Voir aussi

[Page Compiler, Concepteur de projet (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)