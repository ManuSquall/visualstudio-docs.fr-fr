---
title: Personnaliser la façon dont Visual Studio 2015 crée des légendes pour les contrôles liés aux données | Microsoft Docs
titleSuffix: ''
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
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 04f32fa0426039f50c0a0352ef0b04900d705a98
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657438"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Personnaliser la façon dont Visual Studio crée des légendes pour les contrôles liés aux données
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lorsque vous faites glisser des éléments depuis la [fenêtre sources de données](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) vers le Concepteur Windows Forms, une attention particulière est prise en compte : les noms des colonnes dans les étiquettes de légende sont reformatés dans une chaîne plus lisible quand deux mots ou plus sont trouvés pour être concaténés réunis. Vous pouvez personnaliser la façon dont ces étiquettes sont créées, en définissant les valeurs **SmartCaptionExpression**, **SmartCaptionReplacement**et **SmartCaptionSuffix** dans **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\ 10.0 \** clé de registre des concepteurs de données.

> [!NOTE]
> Cette clé de Registre n’existe pas tant que vous ne l’avez pas créée.

 Le sous-titrage intelligent est contrôlé par l’expression régulière entrée dans la valeur de la valeur **SmartCaptionExpression** . L’ajout de la clé de registre des **concepteurs de données** remplace l’expression régulière par défaut qui contrôle les étiquettes de légende. Pour plus d’informations sur les expressions régulières, consultez [utilisation d’expressions régulières dans Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

 Le tableau suivant décrit les valeurs de Registre qui contrôlent les étiquettes de légende.

|Élément de Registre|Description|
|-------------------|-----------------|
|**SmartCaptionExpression**|Expression régulière utilisée pour faire correspondre vos modèles.|
|**SmartCaptionReplacement**|Format d’affichage des groupes correspondants dans le **SmartCaptionExpression**.|
|**SmartCaptionSuffix**|Chaîne facultative à ajouter à la fin de la légende.|

 Le tableau suivant répertorie les paramètres par défaut internes pour ces valeurs de registre.

|Élément de Registre|Valeur par défaut|Explication|
|-------------------|-------------------|-----------------|
|**SmartCaptionExpression**|(\\ \p{Ll}) (\\ \p{Lu}) &#124;_+|Correspond à un caractère minuscule suivi d’un caractère majuscule ou un trait de soulignement.|
|**SmartCaptionReplacement**|$1 $2|$1 représente tous les caractères correspondants dans les premières parenthèses de l’expression, et $2 représente tous les caractères correspondants dans les secondes. Le remplacement correspond à la première correspondance, à un espace, puis à la deuxième correspondance.|
|**SmartCaptionSuffix**|:|Représente un caractère ajouté à la chaîne retournée. Par exemple, si la légende est `Company Name`, le suffixe le rend `Company Name:`|

> [!CAUTION]
> Vous devez être très prudent lorsque vous faites quoi que ce soit dans l’éditeur du Registre. Sauvegardez le registre avant de le modifier. Si vous utilisez l’éditeur du registre de façon incorrecte, vous risquez de provoquer de sérieux problèmes pouvant vous obliger à réinstaller votre système d’exploitation. Microsoft ne garantit pas que les problèmes que vous provoquez à l’aide de l’éditeur du Registre peuvent être résolus de manière incorrecte. Les opérations exécutées dans l'Éditeur du Registre le sont à vos propres risques.
>
> L’article de la base de connaissances suivant contient des instructions pour la sauvegarde, la modification et la restauration du Registre : [Description du Registre Microsoft Windows](http://support.microsoft.com/default.aspx?scid=kb;en-us;256986) (http://support.microsoft.com/default.aspx?scid=kb  ; en-US ; 256986)

### <a name="to-modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>Pour modifier le comportement de la légende intelligente de la fenêtre sources de données

1. Ouvrez une fenêtre de commande en cliquant sur **Démarrer** , puis sur **exécuter**.

2. Tapez `regedit` dans la boîte de dialogue **exécuter** , puis cliquez sur **OK**.

3. Développez le nœud **HKEY_CURRENT_USER** .

4. Développez le nœud **logiciel** .

5. Développez le nœud **Microsoft** .

6. Développez le nœud **VisualStudio** .

7. Cliquez avec le bouton droit sur le nœud **10,0** , puis créez une nouvelle **clé** nommée `Data Designers`.

8. Cliquez avec le bouton droit sur le nœud **concepteurs de données** et créez une **valeur de chaîne** nommée `SmartCaptionExpression`.

9. Cliquez avec le bouton droit sur le nœud **concepteurs de données** et créez une **valeur de chaîne** nommée `SmartCaptionReplacement`.

10. Cliquez avec le bouton droit sur le nœud **concepteurs de données** et créez une **valeur de chaîne** nommée `SmartCaptionSuffix`.

11. Cliquez avec le bouton droit sur l’élément **SmartCaptionExpression** , puis sélectionnez **modifier**.

12. Entrez l’expression régulière que la fenêtre **sources de données** doit utiliser.

13. Cliquez avec le bouton droit sur l’élément **SmartCaptionReplacement** , puis sélectionnez **modifier**.

14. Entrez la chaîne de remplacement mise en forme de la façon dont vous souhaitez afficher les modèles correspondants dans votre expression régulière.

15. Cliquez avec le bouton droit sur l’élément **SmartCaptionSuffix** , puis sélectionnez **modifier**.

16. Entrez les caractères que vous souhaitez voir apparaître à la fin de la légende.

     La prochaine fois que vous faites glisser des éléments depuis la fenêtre **sources de données** , les étiquettes de légende sont créées à l’aide des nouvelles valeurs de Registre fournies.

### <a name="to-turn-off-the-smart-captioning-feature"></a>Pour désactiver la fonctionnalité de légende intelligente

1. Ouvrez une fenêtre de commande en cliquant sur **Démarrer** , puis sur **exécuter**.

2. Tapez `regedit` dans la boîte de dialogue **exécuter** , puis cliquez sur **OK**.

3. Développez le nœud **HKEY_CURRENT_USER** .

4. Développez le nœud **logiciel** .

5. Développez le nœud **Microsoft** .

6. Développez le nœud **VisualStudio** .

7. Cliquez avec le bouton droit sur le nœud **10,0** , puis créez une nouvelle **clé** nommée `Data Designers`.

8. Cliquez avec le bouton droit sur le nœud **concepteurs de données** et créez une **valeur de chaîne** nommée `SmartCaptionExpression`.

9. Cliquez avec le bouton droit sur le nœud **concepteurs de données** et créez une **valeur de chaîne** nommée `SmartCaptionReplacement`.

10. Cliquez avec le bouton droit sur le nœud **concepteurs de données** et créez une **valeur de chaîne** nommée `SmartCaptionSuffix`.

11. Cliquez avec le bouton droit sur l’élément **SmartCaptionExpression** , puis sélectionnez **modifier**.

12. Entrez `(.*)` pour la valeur. Cela correspond à la chaîne entière.

13. Cliquez avec le bouton droit sur l’élément **SmartCaptionReplacement** , puis sélectionnez **modifier**.

14. Entrez `$1` pour la valeur. Cela remplace la chaîne par la valeur correspondante, qui est la chaîne entière afin qu’elle reste inchangée.

     La prochaine fois que vous faites glisser des éléments depuis la fenêtre **sources de données** , les étiquettes de légende sont créées avec des sous-titres non modifiés.

## <a name="see-also"></a>Voir aussi
 [Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
