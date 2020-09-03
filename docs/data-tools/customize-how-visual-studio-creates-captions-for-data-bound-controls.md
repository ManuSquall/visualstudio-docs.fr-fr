---
title: Personnaliser les légendes pour les contrôles liés aux données
ms.date: 11/03/2017
ms.topic: how-to
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 085542f912cc5747c2012adb05e6097b5891ed60
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85282577"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Personnaliser la façon dont Visual Studio crée des légendes pour les contrôles liés aux données

Lorsque vous faites glisser des éléments depuis la [fenêtre sources de données](add-new-data-sources.md#data-sources-window) vers un concepteur, une attention particulière est prise en compte : les noms des colonnes dans les étiquettes de légende sont reformatés dans une chaîne plus lisible quand deux mots ou plus sont trouvés pour être concaténés.

::: moniker range="vs-2017"

Vous pouvez personnaliser la façon dont ces étiquettes sont créées en définissant les valeurs **SmartCaptionExpression**, **SmartCaptionReplacement**et **SmartCaptionSuffix** dans la clé de Registre **HKEY_CURRENT_USER \software\microsoft\visualstudio\15.0\data concepteurs** .

::: moniker-end

::: moniker range=">=vs-2019"

Vous pouvez personnaliser la façon dont ces étiquettes sont créées en définissant les valeurs **SmartCaptionExpression**, **SmartCaptionReplacement**et **SmartCaptionSuffix** dans la clé de Registre **HKEY_CURRENT_USER \software\microsoft\visualstudio\16.0\data concepteurs** .

::: moniker-end

> [!NOTE]
> Cette clé de Registre n’existe pas tant que vous ne l’avez pas créée.

Le sous-titrage intelligent est contrôlé par l’expression régulière entrée dans la valeur de la valeur **SmartCaptionExpression** . L’ajout de la clé de registre des **concepteurs de données** remplace l’expression régulière par défaut qui contrôle les étiquettes de légende. Pour plus d’informations sur les expressions régulières, consultez [utilisation d’expressions régulières dans Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

Le tableau suivant décrit les valeurs de Registre qui contrôlent les étiquettes de légende.

|Élément de Registre|Description|
|-------------------|-----------------|
|**SmartCaptionExpression**|Expression régulière que vous utilisez pour faire correspondre vos modèles.|
|**SmartCaptionReplacement**|Format d’affichage des groupes correspondants dans le **SmartCaptionExpression**.|
|**SmartCaptionSuffix**|Chaîne facultative à ajouter à la fin de la légende.|

Le tableau suivant répertorie les paramètres par défaut internes pour ces valeurs de registre.

|Élément de Registre|Valeur par défaut|Explication|
|-------------------|-------------------|-----------------|
|**SmartCaptionExpression**|**( \\ \p{ll}) ( \\ \p{Lu}) &#124;_ +**|Correspond à un caractère minuscule suivi d’un caractère majuscule ou un trait de soulignement.|
|**SmartCaptionReplacement**|**$1 $2**|**$1** représente tous les caractères correspondants dans les premières parenthèses de l’expression, et **$2** représente tous les caractères correspondants dans les secondes. Le remplacement correspond à la première correspondance, à un espace, puis à la deuxième correspondance.|
|**SmartCaptionSuffix**|**:**|Représente un caractère ajouté à la chaîne retournée. Par exemple, si la légende est `Company Name` , le suffixe le fait `Company Name:`|

> [!CAUTION]
> Soyez très prudent lorsque vous faites quoi que ce soit dans l’éditeur du Registre. Sauvegardez le registre avant de le modifier. Si vous utilisez l’éditeur du registre de façon incorrecte, vous risquez de provoquer de sérieux problèmes pouvant vous obliger à réinstaller votre système d’exploitation. Microsoft ne garantit pas que les problèmes que vous provoquez à l’aide de l’éditeur du Registre peuvent être résolus de manière incorrecte. Utilisez l’Éditeur du Registre à vos propres risques.
>
> Pour plus d’informations sur la sauvegarde, la modification et la restauration du Registre, consultez les [informations du Registre Windows pour les utilisateurs expérimentés](https://support.microsoft.com/help/256986/windows-registry-information-for-advanced-users).

## <a name="modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>Modifier le comportement de la légende intelligente de la fenêtre sources de données

1. Ouvrez une fenêtre de commande en cliquant sur **Démarrer** , puis sur **exécuter**.

2. Tapez `regedit` dans la boîte de dialogue **exécuter** , puis cliquez sur **OK**.

3. Développez le nœud **HKEY_CURRENT_USER**  >  **logiciel**  >  **Microsoft**  >  **VisualStudio** .

::: moniker range="vs-2017"

4. Cliquez avec le bouton droit sur le nœud **15,0** , puis créez une nouvelle **clé** nommée `Data Designers` .

::: moniker-end

::: moniker range=">=vs-2019"

4. Cliquez avec le bouton droit sur le nœud **16,0** , puis créez une nouvelle **clé** nommée `Data Designers` .

::: moniker-end

5. Cliquez avec le bouton droit sur le nœud **concepteurs de données** et créez trois nouvelles valeurs de chaîne :

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

6. Cliquez avec le bouton droit sur la valeur **SmartCaptionExpression** , puis sélectionnez **modifier**.

7. Entrez l’expression régulière que la fenêtre **sources de données** doit utiliser.

8. Cliquez avec le bouton droit sur la valeur **SmartCaptionReplacement** , puis sélectionnez **modifier**.

9. Entrez la chaîne de remplacement mise en forme de la façon dont vous souhaitez afficher les modèles correspondants dans votre expression régulière.

10. Cliquez avec le bouton droit sur la valeur **SmartCaptionSuffix** , puis sélectionnez **modifier**.

11. Entrez les caractères que vous souhaitez voir apparaître à la fin de la légende.

    La prochaine fois que vous faites glisser des éléments depuis la fenêtre **sources de données** , les étiquettes de légende sont créées à l’aide des nouvelles valeurs de Registre fournies.

## <a name="turn-off-the-smart-captioning-feature"></a>Désactiver la fonctionnalité de légende intelligente

1. Ouvrez une fenêtre de commande en cliquant sur **Démarrer** , puis sur **exécuter**.

2. Tapez `regedit` dans la boîte de dialogue **exécuter** , puis cliquez sur **OK**.

3. Développez le nœud **HKEY_CURRENT_USER**  >  **logiciel**  >  **Microsoft**  >  **VisualStudio** .

::: moniker range="vs-2017"

4. Cliquez avec le bouton droit sur le nœud **15,0** , puis créez une nouvelle **clé** nommée `Data Designers` .

::: moniker-end

::: moniker range=">=vs-2019"

4. Cliquez avec le bouton droit sur le nœud **16,0** , puis créez une nouvelle **clé** nommée `Data Designers` .

::: moniker-end

5. Cliquez avec le bouton droit sur le nœud **concepteurs de données** et créez trois nouvelles valeurs de chaîne :

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

6. Cliquez avec le bouton droit sur l’élément **SmartCaptionExpression** , puis sélectionnez **modifier**.

7. Entrez `(.*)` pour la valeur. Cela correspond à la chaîne entière.

8. Cliquez avec le bouton droit sur l’élément **SmartCaptionReplacement** , puis sélectionnez **modifier**.

9. Entrez `$1` pour la valeur. Cela remplace la chaîne par la valeur correspondante, qui est la chaîne entière afin qu’elle reste inchangée.

    La prochaine fois que vous faites glisser des éléments depuis la fenêtre **sources de données** , les étiquettes de légende sont créées avec des sous-titres non modifiés.

## <a name="see-also"></a>Voir aussi

- [Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
