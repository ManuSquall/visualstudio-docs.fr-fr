---
title: "Lier des contrôles WPF à des données dans Visual Studio - partie 1 | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: e05a1e0c-5082-479d-bbc9-d395b0bc6580
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 77c56d70c6fc3dd3dac9a563c146d8bab2c6f699
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Lier des contrôles WPF à des données dans Visual Studio
Vous pouvez afficher des données pour les utilisateurs de votre application en liant des données à des contrôles [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)]. Pour créer ces contrôles liés aux données, vous pouvez faire glisser des éléments à partir de la **des Sources de données** fenêtre sur la [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Cette rubrique décrit quelques tâches, outils et classes les plus courants que vous pouvez utiliser pour créer des applications [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] liées aux données.  
  
 Pour plus d’informations sur la façon de créer des contrôles liés aux données dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], consultez [lier des contrôles aux données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Pour plus d’informations sur [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] liaison de données, consultez [vue d’ensemble de la liaison de données](/dotnet/framework/wpf/data/data-binding-overview).  
  
## <a name="tasks-involved-in-binding-wpf-controls-to-data"></a>Tâches impliquées dans la liaison de contrôles WPF aux données  
 Le tableau suivant répertorie les tâches pouvant être accomplies en faisant glisser des éléments depuis la **des Sources de données** fenêtre pour le [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)].  
  
|Tâche|Complément d'information|  
|----------|----------------------|  
|Créer des contrôles liés aux données.<br /><br /> Lier des contrôles existants à des données.|[Lier des contrôles WPF à un dataset](../data-tools/bind-wpf-controls-to-a-dataset.md)|  
|Créer des contrôles qui affichent les données connexes d'une relation parent-enfant : lorsque l'utilisateur sélectionne un enregistrement de données parentes dans un contrôle, un autre contrôle affiche les données enfants connexes pour l'enregistrement sélectionné.|[Afficher des données associées dans des applications WPF](../data-tools/display-related-data-in-wpf-applications.md)|  
|Créer un *table de recherche* qui affiche des informations à partir d’une table en fonction de la valeur d’un champ de clé étrangère dans une autre table.|[Créer des tables de recherche dans des applications WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)|  
|Lier un contrôle à une image dans une base de données.|[Lier des contrôles à des images d’une base de données](../data-tools/bind-controls-to-pictures-from-a-database.md)|  
  
## <a name="valid-drop-targets"></a>Cibles de déplacement valides  
 Vous pouvez faire glisser des éléments le **des Sources de données** fenêtre uniquement vers les cibles de dépôt valides dans le [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)]. Il existe deux genres principaux de cibles de dépôt valides : conteneurs et contrôles. Un conteneur est un élément d'interface utilisateur qui contient généralement des contrôles. Par exemple, une grille est un conteneur, de même qu'une fenêtre.  
  
## <a name="generated-xaml-and-code"></a>XAML et le code généré  
 Lorsque vous faites glisser un élément à partir de la **des Sources de données** fenêtre pour le [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)], [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] génère [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] qui définit un nouveau contrôle lié aux données (ou lie un contrôle existant à la source de données). Pour certaines sources de données, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] génère également du code dans le fichier code-behind qui remplit la source de données avec les données.  
  
 Le tableau suivant répertorie les [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] ainsi que le code [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] génère pour chaque type de source de données dans le **des Sources de données** fenêtre.  
  
|Source de données|Générer le code XAML qui lie un contrôle à la source de données|Générer du code qui remplit la source de données avec les données|  
|-----------------|-----------------------------------------------------------|--------------------------------------------------------|  
|Groupe de données|Oui|Oui|  
|[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]|Oui|Oui|  
|Service|Oui|Non|  
|Object|Oui|Non|  
  
### <a name="datasets"></a>Groupes de données  
 Lorsque vous faites glisser une table ou une colonne à partir de la **des Sources de données** fenêtre vers le concepteur, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] génère [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] qui effectue les opérations suivantes :  
  
-   Ajoute le groupe de données (dataset) et un nouveau <xref:System.Windows.Data.CollectionViewSource> aux ressources du conteneur vers lequel vous avez fait glisser l'élément. Le <xref:System.Windows.Data.CollectionViewSource> est un objet qui peut être utilisé pour naviguer et pour afficher les données dans le groupe de données.  
  
-   Crée une liaison de données pour un contrôle. Si vous faites glisser l'élément vers un contrôle existant dans le concepteur, le code XAML lie le contrôle à l'élément. Si vous faites glisser l’élément vers un conteneur, le code XAML crée le contrôle qui a été sélectionné pour l’élément déplacé et lie le contrôle à l’élément. Le contrôle est créé dans une nouvelle <xref:System.Windows.Controls.Grid>.  
  
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] apporte également les modifications suivantes au fichier code-behind :  
  
-   Crée un gestionnaire d'événements <xref:System.Windows.FrameworkElement.Loaded> pour l'élément [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] qui contient le contrôle. Le gestionnaire d'événements remplit la table des données, extrait le <xref:System.Windows.Data.CollectionViewSource> des ressources du conteneur, puis active le premier élément de données comme élément de données actuel. Si un <xref:System.Windows.FrameworkElement.Loaded> Gestionnaire d’événements existe déjà, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ajoute ce code au gestionnaire d’événements existant.  
  
### <a name="entity-data-models"></a>Modèles de données d’entité  
 Lorsque vous faites glisser une entité ou une propriété d’entité à partir de la **des Sources de données** fenêtre vers le concepteur, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] génère [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] qui effectue les opérations suivantes :  
  
-   Ajoute un nouveau <xref:System.Windows.Data.CollectionViewSource> aux ressources du conteneur vers lequel vous avez fait glisser l'élément. Le <xref:System.Windows.Data.CollectionViewSource> est un objet qui peut être utilisé pour naviguer et pour afficher les données dans l'entité.  
  
-   Crée une liaison de données pour un contrôle. Si vous faites glisser l'élément vers un contrôle existant dans le concepteur, le code [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] lie le contrôle à l'élément. Si vous faites glisser l’élément à un conteneur, le [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] crée le contrôle qui a été sélectionné pour l’élément déplacé et lie le contrôle à l’élément. Le contrôle est créé dans une nouvelle <xref:System.Windows.Controls.Grid>.  
  
Visual Studio apporte également les modifications suivantes au fichier code-behind :  
  
-   Ajoute une nouvelle méthode qui retourne une requête pour l'entité que vous avez fait glisser vers le concepteur (ou l'entité qui contient la propriété que vous avez fait glisser vers le concepteur). La nouvelle méthode porte le nom Get*EntityName*requête, où *EntityName* est le nom de l’entité.  
  
-   Crée un gestionnaire d'événements <xref:System.Windows.FrameworkElement.Loaded> pour l'élément [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] qui contient le contrôle. Le Gestionnaire d’événements appelle la méthode Get*EntityName*requête de méthode pour remplir l’entité des données, extrait le <xref:System.Windows.Data.CollectionViewSource> à partir du conteneur ressources, puis rend les premier élément de données l’élément actuel. Si un <xref:System.Windows.FrameworkElement.Loaded> Gestionnaire d’événements existe déjà, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ajoute ce code au gestionnaire d’événements existant.  
  
### <a name="services"></a>Services  
 Lorsque vous faites glisser un objet de service ou une propriété à partir de la **des Sources de données** fenêtre vers le concepteur, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] génère [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] qui crée un contrôle lié aux données (ou lie un contrôle existant à l’objet ou la propriété). Toutefois, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ne génère pas de code qui remplit l'objet de service proxy avec les données. Vous devez écrire ce code vous-même. Pour obtenir un exemple qui montre comment effectuer cette opération, consultez [WPF de lier des contrôles à un service de données WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).  
  
 Visual Studio génère du code XAML qui effectue les opérations suivantes :  
  
-   Ajoute un nouveau <xref:System.Windows.Data.CollectionViewSource> aux ressources du conteneur vers lequel vous avez fait glisser l'élément. Le <xref:System.Windows.Data.CollectionViewSource> est un objet qui peut être utilisé pour naviguer et pour afficher les données dans l'objet retourné par le service.  
  
-   Crée une liaison de données pour un contrôle. Si vous faites glisser l'élément vers un contrôle existant dans le concepteur, le code [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] lie le contrôle à l'élément. Si vous faites glisser l’élément à un conteneur, le [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] crée le contrôle qui a été sélectionné pour l’élément déplacé et lie le contrôle à l’élément. Le contrôle est créé dans une nouvelle <xref:System.Windows.Controls.Grid>.  
  
### <a name="objects"></a>Objets  
 Lorsque vous faites glisser un objet ou une propriété à partir de la **des Sources de données** fenêtre vers le concepteur, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] génère [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] qui crée un contrôle lié aux données (ou lie un contrôle existant à l’objet ou la propriété). Toutefois, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ne génère pas de code pour remplir l'objet avec les données. Vous devez écrire ce code vous-même.  
  
> [!NOTE]
>  Classes personnalisées doivent être public et, par défaut, avoir un constructeur sans paramètre. Ils classes can'tbe imbriquées qui ont un « point » dans leur syntaxe. Pour plus d’informations, consultez [XAML et Classes personnalisées pour WPF](/dotnet/framework/wpf/advanced/xaml-and-custom-classes-for-wpf).  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]génère [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] qui effectue les opérations suivantes :  
  
-   Ajoute un nouveau <xref:System.Windows.Data.CollectionViewSource> aux ressources du conteneur vers lequel vous avez fait glisser l'élément. Le <xref:System.Windows.Data.CollectionViewSource> est un objet qui peut être utilisé pour naviguer et pour afficher les données dans l'objet.  
  
-   Crée une liaison de données pour un contrôle. Si vous faites glisser l'élément vers un contrôle existant dans le concepteur, le code XAML lie le contrôle à l'élément. Si vous faites glisser l’élément vers un conteneur, le code XAML crée le contrôle qui a été sélectionné pour l’élément déplacé et lie le contrôle à l’élément. Le contrôle est créé dans une nouvelle <xref:System.Windows.Controls.Grid>.  
  
## <a name="see-also"></a>Voir aussi
[Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
