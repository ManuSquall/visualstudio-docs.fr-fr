---
title: Lier des contrôles WPF à des données (partie 2) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 00dd5147-db0b-4b59-8d6c-8229b09ca9dd
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 06428a633aec41489a8a77655d6ea9442ffffaa0
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540086"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Lier des contrôles WPF à des données dans Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez créer des contrôles liés aux données à [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] l’aide de la fenêtre **sources de données** . Tout d’abord, ajoutez une source de données à la fenêtre **sources de données** . Ensuite, faites glisser des éléments de la fenêtre **sources de données** vers le**Concepteur WPF**.

## <a name="add-a-data-source-to-the-data-sources-window"></a><a name="adding"></a>Ajouter une source de données à la fenêtre sources de données
 Avant de pouvoir créer des contrôles liés aux données, vous devez d’abord ajouter une source de données à la fenêtre **sources de données** .

#### <a name="to-add-a-data-source-to-the-data-sources-window"></a>Pour ajouter une source de données à la fenêtre Sources de données

1. Dans le menu **affichage** , pointez sur **autres fenêtres**, puis cliquez sur **sources de données**.

2. Cliquez sur **Ajouter une nouvelle source de données** et suivez les étapes de l’Assistant **Configuration de source de données**.

3. Effectuez l’une des tâches suivantes pour créer des contrôles liés aux données :

    - [Création d’un contrôle lié à un seul champ de données](#simple).

    - [Création d’un contrôle lié à plusieurs champs de données](#complex).

    - [Création d’un ensemble de contrôles liés à plusieurs champs de données](#details).

    - [Liaison de données à des contrôles existants dans le concepteur](#existing).

## <a name="create-a-control-that-is-bound-to-a-single-field-of-data"></a><a name="simple"></a>Créer un contrôle lié à un seul champ de données
 Après avoir ajouté une source de données à la fenêtre **sources de données** , vous pouvez créer un contrôle lié aux données qui affiche un seul champ de données, tel que <xref:System.Windows.Controls.ComboBox> ou <xref:System.Windows.Controls.TextBox> .

#### <a name="to-create-a-control-that-is-bound-to-a-single-field-of-data"></a>Pour créer un contrôle lié à un seul champ de données

1. Dans la fenêtre **sources de données** , développez un élément qui représente une table ou un objet. Recherchez l'élément enfant représentant la colonne ou la propriété que vous voulez lier. Pour obtenir un exemple visuel, consultez [data sources Window](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

2. Sélectionnez éventuellement le contrôle à créer. Chaque élément de la fenêtre **sources de données** a un contrôle par défaut qui est créé lorsque vous faites glisser l’élément vers le concepteur. Le contrôle par défaut dépend du type de données sous-jacent de l'élément.

     Pour choisir un autre contrôle, cliquez sur la flèche déroulante à côté de l’élément et sélectionnez un contrôle. Pour plus d’informations, consultez [définir le contrôle à créer lors d’une opération de glisser-déplacer à partir de la fenêtre sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

3. Faites glisser l’élément vers un conteneur valide dans le concepteur. Pour plus d’informations sur les conteneurs valides, consultez [lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]crée le nouveau contrôle lié aux données et un intitulé approprié <xref:System.Windows.Controls.Label> dans le conteneur. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]génère également [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] et le code pour lier le contrôle aux données. Pour plus d’informations, consultez [lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

## <a name="create-a-control-that-is-bound-to-multiple-fields-of-data"></a><a name="complex"></a>Créer un contrôle lié à plusieurs champs de données
 Après avoir ajouté une source de données à la fenêtre **sources de données** , vous pouvez créer un contrôle lié aux données qui affiche plusieurs champs de données, tel que <xref:System.Windows.Controls.DataGrid> ou <xref:System.Windows.Controls.ListView> .

#### <a name="to-create-a-control-that-is-bound-to-multiple-fields-of-data"></a>Pour créer un contrôle lié à plusieurs champs de données

1. Dans la fenêtre **sources de données** , sélectionnez un élément qui représente une table ou un objet. Pour obtenir un exemple visuel, consultez [data sources Window](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

2. Sélectionnez éventuellement le contrôle à créer. Par défaut, chaque élément de la fenêtre **sources de données** qui représente une table de données ou un objet est défini pour créer un <xref:System.Windows.Controls.DataGrid> (si votre projet cible .NET Framework 4) ou <xref:System.Windows.Controls.ListView> (pour les versions antérieures du .NET Framework).

     Pour choisir un autre contrôle, cliquez sur la flèche déroulante à côté de l'élément et sélectionnez un contrôle. Pour plus d’informations, consultez [définir le contrôle à créer lors d’une opération de glisser-déplacer à partir de la fenêtre sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

    > [!NOTE]
    > Si vous ne voulez pas afficher une colonne ou propriété particulière, développez l’élément pour afficher ses enfants. Cliquez sur la flèche déroulante en regard de la colonne ou de la propriété que vous ne souhaitez pas afficher, puis cliquez sur **aucun**.

3. Faites glisser l'élément vers un conteneur valide du concepteur, comme <xref:System.Windows.Controls.Grid>. Pour plus d’informations sur les conteneurs valides, consultez [lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]crée le contrôle lié aux données dans le conteneur. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]génère également [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] et le code pour lier le contrôle aux données. Pour plus d’informations, consultez [lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

## <a name="create-a-set-of-controls-that-are-bound-to-multiple-fields-of-data"></a><a name="details"></a>Créer un ensemble de contrôles liés à plusieurs champs de données
 Après avoir ajouté une source de données à la fenêtre **sources de données** , vous pouvez lier une table de données ou un objet à un ensemble de contrôles. Un autre contrôle est créé pour chaque colonne ou propriété dans la table ou l'objet.

#### <a name="to-create-a-set-of-controls-that-are-bound-to-multiple-fields-of-data"></a>Pour créer un ensemble de contrôles liés à plusieurs champs de données

1. Dans la fenêtre **sources de données** , sélectionnez un élément qui représente une table ou un objet. Pour obtenir un exemple visuel, consultez [data sources Window](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

2. Cliquez sur la flèche déroulante à côté de l’élément et sélectionnez **Détails**.

    > [!NOTE]
    > Si vous ne voulez pas afficher une colonne ou propriété particulière, développez l’élément pour afficher ses enfants. Cliquez sur la flèche déroulante en regard de la colonne ou de la propriété que vous ne souhaitez pas afficher, puis cliquez sur **aucun**.

3. Faites glisser l'élément vers un conteneur valide du concepteur, comme <xref:System.Windows.Controls.Grid>. Pour plus d’informations sur les conteneurs valides, consultez [lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]crée les nouveaux contrôles liés aux données dans le conteneur. Chaque contrôle est lié à une colonne ou propriété différente, et chaque contrôle est accompagné d’un contrôle correctement intitulé <xref:System.Windows.Controls.Label> . [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]génère également [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] et le code pour lier les contrôles aux données. Pour plus d’informations, consultez [lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

## <a name="binddata-to-existing-controls-in-the-designer"></a><a name="existing"></a>BindData à des contrôles existants dans le concepteur
 Après avoir ajouté une source de données à la fenêtre **sources de données** , vous pouvez ajouter une liaison de données à un contrôle existant dans le concepteur.

#### <a name="to-bind-data-to-an-existing-control-in-the-designer"></a>Pour lier des données à un contrôle existant dans le concepteur

1. Dans la fenêtre **sources de données** , utilisez l’une des procédures suivantes :

    - Pour ajouter une liaison de données à un contrôle existant affichant plusieurs champs de données, tel que <xref:System.Windows.Controls.DataGrid> ou <xref:System.Windows.Controls.ListView>, sélectionnez l'élément représentant la table ou l'objet que vous voulez lier au contrôle.

    - Pour ajouter une liaison de données à un contrôle existant affichant un seul champ de données, tel que <xref:System.Windows.Controls.ComboBox> ou <xref:System.Windows.Controls.TextBox>, développez l'élément représentant la table ou l'objet qui contient les données, puis sélectionnez l'élément représentant les données à lier au contrôle.

2. Faites glisser l’élément sélectionné de la fenêtre **sources de données** vers un contrôle existant dans le concepteur. Le contrôle doit être une cible de déplacement valide. Pour plus d’informations, consultez [lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]génère [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] et le code pour lier le contrôle aux données. Pour plus d’informations, consultez [lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

    > [!NOTE]
    > Si le contrôle est déjà lié aux données, la liaison de données pour le contrôle est redéfinie sur l’élément qui a été le plus récemment déplacé vers le contrôle.

## <a name="see-also"></a>Voir aussi
 [Lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [créer des tables de recherche dans des applications WPF](../data-tools/create-lookup-tables-in-wpf-applications.md) [afficher des données associées dans des applications WPF](../data-tools/display-related-data-in-wpf-applications.md) [lier des contrôles WPF à un DataSet](../data-tools/bind-wpf-controls-to-a-dataset.md) [lier des contrôles WPF à une](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) [procédure pas à pas de service de données WCF : affichage de données connexes dans une application WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)
