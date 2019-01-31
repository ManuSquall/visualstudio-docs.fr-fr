---
title: Paramètres avancés du compilateur, boîte de dialogue (Visual Basic) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAdvancedCompile
helpviewer_keywords:
- Advanced Compiler Settings dialog box
ms.assetid: 1f81133a-293f-4dba-bc1c-8baafb01d857
caps.latest.revision: 52
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1c1932f3b9a065115c7977207b0678fbcd44c2e4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54758885"
---
# <a name="advanced-compiler-settings-dialog-box-visual-basic"></a>Paramètres avancés du compilateur, boîte de dialogue (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Utilisez la boîte de dialogue **Paramètres avancés du compilateur** du **Concepteur de projets** pour spécifier les propriétés de configuration de build avancées du projet. Cette boîte de dialogue s’applique uniquement aux projets Visual Basic.  
  
### <a name="to-access-this-dialog-box"></a>Pour accéder à cette boîte de dialogue  
  
1. Dans l’**Explorateur de solutions**, choisissez un nœud de projet (pas le nœud **Solution**).  
  
2. Dans le menu **Projet**, cliquez sur **Propriétés**. Quand le **Concepteur de projets** apparaît, cliquez sur l’onglet **Compiler**.  
  
3. Dans la [page Compiler, Concepteur de projets (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md), sélectionnez **Configuration** et **Plateforme**. Dans les configurations de build simplifiées, les listes **Configuration** et **Plateforme**  ne sont pas affichées. Pour plus d’informations, consultez [Configurations de projet Debug et Release](http://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).  
  
4. Cliquez sur **Options avancées de compilation**.  
  
   [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]  
  
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
 Les constantes de compilation conditionnelle reviennent à utiliser une directive de préprocesseur [#Const](http://msdn.microsoft.com/library/707669e5-23f9-4f17-8622-a0d534429386) dans un fichier source, sauf que les constantes définies sont publiques et s’appliquent à tous les fichiers du projet. Vous pouvez utiliser des constantes de compilation conditionnelle avec la directive [#If...Then...#Else](http://msdn.microsoft.com/library/10bba104-e3fd-451b-b672-faa472530502) pour compiler des fichiers sources de façon conditionnelle. Consultez [Compilation conditionnelle](http://msdn.microsoft.com/library/9c35e55e-7eee-44fb-a586-dad1f1884848).  
  
 **Définir la constante DEBUG**  
 Par défaut, cette case est cochée, spécifiant qu’une constante DEBUG est définie.  
  
 **Définir la constante TRACE**  
 Par défaut, cette case est cochée, spécifiant qu’une constante TRACE est définie.  
  
 **Constantes personnalisées**  
 Entrez les constantes personnalisées pour votre application dans cette zone de texte. Les entrées doivent être délimitées par des virgules, au format suivant : **Nom1="Valeur1",Nom2="Valeur2",Nom3="Valeur3"**.  
  
## <a name="other-settings"></a>Autres paramètres  
 **Générer des assemblys de sérialisation**  
 Ce paramètre spécifie si le compilateur crée des assemblys de sérialisation XML. Les assemblys de sérialisation peuvent améliorer les performances de démarrage de <xref:System.Xml.Serialization.XmlSerializer> si vous avez utilisé cette classe pour sérialiser les types dans votre code. Par défaut, cette option a la valeur **Auto**, qui spécifie que les assemblys de sérialisation ne peuvent être générés que si vous avez utilisé <xref:System.Xml.Serialization.XmlSerializer> pour encoder les types dans votre code en XML. **Inactif** spécifie que les assemblys de sérialisation ne doivent jamais être générés, que votre code utilise <xref:System.Xml.Serialization.XmlSerializer> ou non. **Actif** spécifie que les assemblys de sérialisation doivent toujours être générés. Les assemblys de sérialisation sont appelés `TypeName`.XmlSerializers.dll.  
  
## <a name="see-also"></a>Voir aussi  
 [Page Compiler, Concepteur de projet (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
