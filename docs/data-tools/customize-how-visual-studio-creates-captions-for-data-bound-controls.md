---
title: Personnaliser la façon dont Visual Studio crée des légendes pour les contrôles liés aux données
ms.date: 11/03/2017
ms.topic: conceptual
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 69e97efe6db8b06f476b7dc004e3b52a77701cb0
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758418"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Personnaliser la façon dont Visual Studio crée des légendes pour les contrôles liés aux données

Lorsque vous faites glisser des éléments à partir de la [fenêtre Sources de données](add-new-data-sources.md) sur un concepteur, une attention particulière entre en jeu : les noms de colonnes dans les légendes sont reformatés dans une chaîne plus lisible lorsque deux ou plusieurs mots sont identifiés comme étant concaténées. Vous pouvez personnaliser la façon dans lequel ces étiquettes sont créés en définissant le **SmartCaptionExpression**, **SmartCaptionReplacement**, et **SmartCaptionSuffix** des valeurs dans le **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Data concepteurs** clé de Registre.

> [!NOTE]
> Cette clé de Registre n’existe pas jusqu'à ce que vous la créez.

Sous-titrage intelligente est contrôlé par l’expression régulière entrée dans la valeur de la **SmartCaptionExpression** valeur. Ajout de la **concepteurs de données** clé de Registre remplace l’expression régulière par défaut qui contrôle les étiquettes de légende. Pour plus d’informations sur les expressions régulières, consultez [à l’aide d’expressions régulières dans Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

Le tableau suivant décrit les valeurs de Registre qui contrôlent les étiquettes de légende.

|Élément de Registre|Description|
|-------------------|-----------------|
|**SmartCaptionExpression**|L’expression régulière que vous permet de correspondre à vos modèles.|
|**SmartCaptionReplacement**|Le format d’affichage des groupes de mise en correspondance dans le **SmartCaptionExpression**.|
|**SmartCaptionSuffix**|Chaîne facultative à ajouter à la fin de la légende.|

Le tableau suivant répertorie les paramètres internes par défaut pour ces valeurs de Registre.

|Élément de Registre|Valeur par défaut|Explication|
|-------------------|-------------------|-----------------|
|**SmartCaptionExpression**|**(\\\p{Ll}) (\\\p{Lu})&#124;_ +**|Correspond à un caractère minuscule suivi d’un caractère majuscule ou un trait de soulignement.|
|**SmartCaptionReplacement**|**$1 $2**|Le **$1** représente les caractères appariés dans la première parenthèse de l’expression et le **$2** représente les caractères appariés dans la deuxième parenthèse. Le remplacement est la première correspondance, un espace, puis la deuxième correspondance.|
|**SmartCaptionSuffix**|**:**|Représente un caractère ajouté à la chaîne retournée. Par exemple, si la légende est `Company Name`, rend le suffixe `Company Name:`|

> [!CAUTION]
> Vous devez être très prudent lorsque vous sert à rien dans l’Éditeur du Registre. Sauvegardez le Registre avant de le modifier. Si vous utilisez l’Éditeur du Registre de manière incorrecte, vous pouvez provoquer de graves problèmes qui peuvent vous obliger à réinstaller votre système d’exploitation. Microsoft ne garantit pas que les problèmes qui vous entraîner à l’aide de l’Éditeur du Registre incorrecte peuvent être résolus. Les opérations exécutées dans l'Éditeur du Registre le sont à vos propres risques.
>
> L’article suivant de la base de connaissances contient des instructions pour la sauvegarde, la modification et la restauration du Registre : [Description du Registre Microsoft Windows](http://support.microsoft.com/default.aspx?scid=kb;en-us;256986) (http://support.microsoft.com/default.aspx?scid=kb; en-us ; 256986)

## <a name="modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>Modifier le comportement de sous-titrage intelligent de la fenêtre Sources de données

1.  Ouvrez une fenêtre de commande en cliquant sur **Démarrer** , puis **exécuter**.

2.  Type `regedit` dans le **exécuter** boîte de dialogue, puis cliquez sur **OK**.

3.  Développez le **HKEY_CURRENT_USER** > **logiciel** > **Microsoft** > **VisualStudio**nœud.

7.  Avec le bouton droit le **15.0** nœud, puis créez un **clé** nommé `Data Designers`.

8.  Avec le bouton droit le **concepteurs de données** nœud et créer trois nouvelles valeurs de chaîne :

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

11. Cliquez sur le **SmartCaptionExpression** valeur, puis sélectionnez **modifier**.

12. Entrez l’expression régulière que vous souhaitez que le **des Sources de données** fenêtre à utiliser.

13. Cliquez sur le **SmartCaptionReplacement** valeur, puis sélectionnez **modifier**.

14. Entrez le remplacement de la chaîne mise en forme comme vous le souhaitez afficher les modèles mis en correspondance dans votre expression régulière.

15. Cliquez sur le **SmartCaptionSuffix** valeur, puis sélectionnez **modifier**.

16. Entrez les caractères que vous souhaitez voir apparaître à la fin de la légende.

    La prochaine fois que vous faites glisser des éléments à partir de la **des Sources de données** fenêtre, les étiquettes de légende sont créés à l’aide des nouvelles valeurs de Registre fournies.

## <a name="turn-off-the-smart-captioning-feature"></a>Désactiver la fonctionnalité de sous-titrage intelligente

1.  Ouvrez une fenêtre de commande en cliquant sur **Démarrer** , puis **exécuter**.

2.  Type `regedit` dans le **exécuter** boîte de dialogue, puis cliquez sur **OK**.

3.  Développez le **HKEY_CURRENT_USER** > **logiciel** > **Microsoft** > **VisualStudio**nœud.

7.  Avec le bouton droit le **15.0** nœud, puis créez un **clé** nommé `Data Designers`.

8.  Avec le bouton droit le **concepteurs de données** nœud et créer trois nouvelles valeurs de chaîne :

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

11. Cliquez sur le **SmartCaptionExpression** d’élément, puis sélectionnez **modifier**.

12. Entrez `(.*)` pour la valeur. Il correspond à la chaîne entière.

13. Cliquez sur le **SmartCaptionReplacement** d’élément, puis sélectionnez **modifier**.

14. Entrez `$1` pour la valeur. Cela remplace la chaîne avec la valeur mise en correspondance, ce qui est la chaîne entière afin qu’elle reste inchangée.

    La prochaine fois que vous faites glisser des éléments à partir de la **des Sources de données** fenêtre, les étiquettes de légende sont créés avec des légendes non modifiées.

## <a name="see-also"></a>Voir aussi

- [Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)