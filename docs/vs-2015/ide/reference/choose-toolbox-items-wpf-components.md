---
title: Choisir des éléments de boîte à outils, Composants WPF | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.chooseitems.wpfcomponents
helpviewer_keywords:
- WPF Components tab, Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box, WPF Components tab
ms.assetid: 6ce1d178-88c0-4295-8915-59fdeedabb11
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4cbfaea72633f6f4bbeb7da3bf6e7c02069889f9
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59647700"
---
# <a name="choose-toolbox-items-wpf-components"></a>Choisir des éléments de boîte à outils, Composants WPF
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cet onglet de la boîte de dialogue **Choisir des éléments de boîte à outils** affiche la liste des contrôles Windows Presentation Foundation (WPF) disponibles sur votre ordinateur local. Pour afficher la liste, sélectionnez **Choisir des éléments de boîte à outils** dans le menu **Outils** pour afficher la boîte de dialogue **Choisir des éléments de boîte à outils**, puis sélectionnez l’onglet **Composants WPF**. Pour trier la liste des composants, cliquez sur un en-tête de colonne.  
  
- Lorsque la case en regard d’un composant est cochée, une icône de ce composant s’affiche dans la **boîte à outils**.  
  
  > [!TIP]
  >  Pour ajouter une instance d’un contrôle WPF à un document de projet ouvert pour modification, faites glisser son icône de **boîte à outils** vers le mode Création. Le balisage et le code par défaut du composant sont insérés dans votre projet, prêts à être modifiés. Pour plus d’informations, consultez [Comment : gérer la fenêtre Boîte à outils](http://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2) et [Comment : manipuler des onglets de boîte à outils](http://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db).  
  
- Lorsque la case en regard d’un composant est décochée, l’icône correspondante est retirée de la **boîte à outils**.  
  
  > [!NOTE]
  >  Les composants .NET Framework installés sur votre ordinateur restent disponibles, même si leurs icônes ne s’affichent pas dans la **boîte à outils**.  
  
  Les colonnes de l’onglet **Composants WPF** contient les informations suivantes :  
  
  Name  
  Répertorie les noms des contrôles WPF dont les entrées correspondantes se trouvent dans le Registre de votre ordinateur.  
  
  Espace de noms  
  Affiche la hiérarchie de l’espace de noms de la [bibliothèque de classes .NET Framework](http://msdn.microsoft.com/6c4f3a62-6a0f-41f2-9d52-ee0b13686f29) qui définit la structure du composant. Triez cette colonne pour répertorier les composants disponibles dans chaque espace de noms .NET Framework installé sur votre ordinateur.  
  
  Nom de l'assembly  
  Affiche le nom de l’assembly .NET Framework qui comprend l’espace de noms de chaque composant. Triez cette colonne pour répertorier les espaces de noms contenus dans chaque assembly .NET Framework installé sur votre ordinateur.  
  
  Répertoire  
  Affiche l’emplacement de l’assembly .NET Framework. L'emplacement par défaut de tous les assemblys est le Global Assembly Cache. Pour plus d’informations sur le Global Assembly Cache, consultez [Utilisation d’assemblys et du Global Assembly Cache](http://msdn.microsoft.com/library/8a18e5c2-d41d-49ef-abcb-7c27e2469433).  
  
## <a name="uielement-list"></a>Liste des éléments d’interface  
 **Filtrer**  
 Filtre la liste des contrôles WPF en fonction de la chaîne que vous entrez dans la zone de texte. Toutes les correspondances des quatre colonnes sont affichées.  
  
 **Effacer**  
 Efface la chaîne de filtrage.  
  
 **Parcourir**  
 Ouvre la boîte de dialogue **Ouvrir** qui permet d’accéder aux assemblys contenant des contrôles WPF. Utilisez cette boîte de dialogue pour charger les assemblys qui ne se trouvent pas dans le Global Assembly Cache.  
  
 **Language**  
 Affiche la langue localisée de l’assembly qui contient le contrôle WPF sélectionné.  
  
## <a name="limitations"></a>Limitations  
 L’ajout d’un contrôle personnalisé ou d’un <xref:System.Windows.Controls.UserControl> à la boîte à outils présente les limitations suivantes.  
  
- Cela fonctionne uniquement pour les contrôles personnalisés définis en dehors du projet actuel.  
  
- Cela ne permet pas une mise à jour correcte lorsque vous passez d’une configuration de solution Debug à une configuration Release, et inversement. Cela est dû au fait que la référence n’est pas une référence de projet, mais une référence à l’assembly sur disque. Si le contrôle fait partie de la solution actuelle, lorsque vous passez de Debug à Release, votre projet continue à référencer la version Debug du contrôle.  
  
  En outre, si les métadonnées au moment du design sont appliquées au contrôle personnalisé et si ces métadonnées spécifient que <xref:Microsoft.Windows.Design.ToolboxBrowsableAttribute> a la valeur `false`, le contrôle n’apparaît pas dans la boîte à outils.  
  
  Vous pouvez référencer directement vos contrôles dans la vue XAML en mappant l’espace de noms et l’assembly de votre contrôle. Pour plus d’informations, consultez [Comment : importer un espace de noms en XAML](http://msdn.microsoft.com/6cda7c7a-369c-47dd-9c2d-13a35dcf737c).  
  
## <a name="see-also"></a>Voir aussi  
 [Choisir des éléments de boîte à outils, boîte de dialogue (Visual Studio)](http://msdn.microsoft.com/bd07835f-18a8-433e-bccc-7141f65263bb)   
 [Boîte à outils](../../ide/reference/toolbox.md)   
 [Comment : utiliser un contrôle WPF tiers dans une application WPF](http://msdn.microsoft.com/f4c0b601-3818-4f9f-85e5-77905f3b427f)   
 [Concepteur WPF](http://msdn.microsoft.com/c6c65214-8411-4e16-b254-163ed4099c26)
