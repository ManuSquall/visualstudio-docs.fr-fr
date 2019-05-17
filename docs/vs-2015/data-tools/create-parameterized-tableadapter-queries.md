---
title: Créer des requêtes TableAdapter paramétrées
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- TableAdapters, parameterized queries
- data [Visual Studio], searching data
- queries [Visual Studio], creating
- TableAdapters, searching data
- queries [Visual Studio], TableAdapters
ms.assetid: 104d1d19-b5a9-4071-b81e-1b3af08e9c7b
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1da058cbbdda71758e9a158cfd6778a044797093
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703826"
---
# <a name="create-parameterized-tableadapter-queries"></a>Créer des requêtes TableAdapter paramétrées
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Une requête paramétrable retourne des données remplissant les conditions d'une clause WHERE dans la requête. Par exemple, vous pouvez paramétrer une liste de clients de sorte à n'afficher que les clients d'une certaine ville en ajoutant `WHERE City = @City` à la fin de l'instruction SQL qui retourne une liste de clients.  
  
Vous créez des requêtes TableAdapter paramétrées dans le Concepteur de Dataset. Vous pouvez également les créer dans une application Windows avec le **paramétrer la Source de données** commande sur le **données** menu. Le **paramétrer la Source de données** commande crée des contrôles sur votre formulaire où vous pouvez entrer les valeurs de paramètre et exécuter la requête.  
  
> [!NOTE]
> Lors de la construction d’une requête paramétrée, utilisez la notation de paramètre spécifique à la base de données que vous codez par rapport à. Par exemple, les sources de données Access et OleDb utilisent le point d'interrogation « ? » pour désigner des paramètres, la clause WHERE sera donc de type : `WHERE City = ?`.  
  
> [!NOTE]
> Les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles décrites dans l’aide, en fonction de vos paramètres actifs ou de l’édition que vous utilisez. Pour modifier vos paramètres, accédez à la **outils** menu et sélectionnez **importation et exportation de paramètres**. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="create-a-parameterized-tableadapter-query"></a>Créer une requête TableAdapter paramétrée 
  
- Créez un TableAdapter, en ajoutant une clause WHERE avec les paramètres souhaités à l'instruction SQL. Pour plus d’informations, consultez [créer et configurer des TableAdapters](../data-tools/create-and-configure-tableadapters.md).  
  
     ou  
  
- Ajoutez une requête à un TableAdapter existant, en ajoutant une clause WHERE avec les paramètres souhaités à l'instruction SQL.
  
### <a name="create-a-parameterized-query-while-designing-a-data-bound-form"></a>Créer une requête paramétrable lors de la création d’un formulaire lié aux données  
  
1. Sélectionnez un contrôle dans votre formulaire déjà lié à un dataset. Pour plus d’informations, consultez [lier les formulaires Windows contrôle aux données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).  
  
2. Sur le **données** menu, sélectionnez**ajouter une requête**.  
  
3. Utilisez la boîte de dialogue **Générateur de critères de recherche**, en ajoutant une clause WHERE avec les paramètres souhaités à l’instruction SQL.  
  
### <a name="add-a-query-to-an-existing-data-bound-form"></a>Ajouter une requête à un formulaire lié aux données existant  
  
1. Ouvrez le formulaire dans le **Concepteur Windows Forms**.  
  
2. Sur le **données** menu, sélectionnez **ajouter une requête** ou **balises actives de données**.  
  
   > [!NOTE]
   > Si l’option **Ajouter une requête** n’est pas disponible dans le menu **Données**, sélectionnez un contrôle dans le formulaire qui affiche la source de données à laquelle ajouter le paramétrage. Par exemple, si le formulaire affiche des données dans un contrôle <xref:System.Windows.Forms.DataGridView>, sélectionnez-le. Si le formulaire affiche des données dans des contrôles individuels, sélectionnez n'importe quel contrôle lié aux données.  
  
3. Dans le **table de source de données Sélectionnez** zone, sélectionnez le tablethat que vous souhaitez ajouter le paramétrage à.  
  
4. Tapez un nom dans la zone **Nom de la nouvelle requête** si vous créez une requête.  
  
    ou  
  
    Sélectionnez une requête dans la zone **Nom de la requête existante**.  
  
5. Dans le **texte de la requête** , tapez une requête qui accepte des paramètres.  
  
6. Sélectionnez **OK**.  
  
    Un contrôle pour entrer le paramètre et un bouton **Charger** sont ajoutés au formulaire dans un contrôle <xref:System.Windows.Forms.ToolStrip>.  
  
   Les valeurs null peuvent être assignées aux paramètres TableAdapter lorsque vous souhaitez interroger les enregistrements qui n’ont aucune valeur actuelle. Par exemple, considérez la requête suivante qui a un `ShippedDate` paramètre dans son `WHERE` clause :  
  
   ```sql
   SELECT CustomerID, OrderDate, ShippedDate  
   FROM Orders  
   WHERE (ShippedDate = @ShippedDate) OR  
   (ShippedDate IS NULL)  
   ```

S’il s’agissait d’une requête sur un TableAdapter, vous pouvez rechercher toutes les commandes qui n’ont pas été fournis par le code suivant :  
  
   [!code-csharp[VbRaddataTableAdapters#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Form2.cs#8)]
   [!code-vb[VbRaddataTableAdapters#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Form2.vb#8)]  
  
### <a name="enable-a-query-to-accept-null-values"></a>Activer une requête d’accepter les valeurs null  
  
1. Dans le **Concepteur de Dataset**, sélectionnez la requête TableAdapter qui doit accepter les valeurs de paramètre null.  
  
2. Dans le **propriétés** fenêtre, sélectionnez **paramètres**. Appuyez sur le bouton de sélection (**...** ) pour ouvrir la **éditeur de collections Parameters**.  
  
3. Sélectionnez le paramètre qui autorise les valeurs null et définissez le **AllowDbNull** propriété `true`.  
  
## <a name="see-also"></a>Voir aussi

- [Remplir des datasets à l’aide de TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)