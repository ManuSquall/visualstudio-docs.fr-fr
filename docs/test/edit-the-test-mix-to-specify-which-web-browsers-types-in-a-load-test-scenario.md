---
title: Combinaison de tests de navigateur pour les tests de charge dans Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, web browser types
- load tests, scenarios
- load tests, adding browsers
- load tests, removing browsers
ms.assetid: 47f981d9-3038-45cc-a486-82b9daf9a9a1
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: be0bd036c907f852028f6a9cccc798742e624184
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario"></a>Modifier la combinaison de tests pour spécifier les types de navigateur web dans un scénario de test de charge

La *combinaison de navigateurs* vous permet de simuler une charge avec plus de réalisme dans un scénario de test de charge. La charge est générée à l'aide d'une combinaison hétérogène de navigateurs Web au lieu d'un seul navigateur Web. Vous créez une approximation plus proche des navigateurs Web qui seront utilisés avec vos applications.

 Une combinaison de navigateurs spécifie la probabilité qu'un utilisateur virtuel exécute un type de navigateur Web particulier dans un scénario de test de charge. Lorsque vous créez un test de charge, vous pouvez souhaiter simuler le fait que cette charge soit générée par le biais de plusieurs navigateurs Web. Lorsque vous ajoutez un type de navigateur Web à la combinaison à partir de l'ensemble de navigateurs Web fourni, un ensemble d'en-têtes associés pour le navigateur Web sélectionné est ajouté à chaque requête HTTP envoyée par un test de performances de site Web.

 La combinaison de navigateurs fonctionne comme d'autres options de combinaison. Un type de navigateur Web est associé de manière aléatoire à un utilisateur virtuel, selon la combinaison de navigateurs. Les tests de cet utilisateur sont exécutés sur un navigateur Web particulier, selon la probabilité que vous avez spécifiée dans la combinaison.

 Après avoir spécifié une combinaison de navigateurs, vous pouvez ajouter et supprimer ultérieurement des types de navigateurs Web à la combinaison. Vous pouvez également modifier la distribution de la combinaison de navigateurs en utilisant le contrôle de combinaison. Le contrôle de combinaison vous permet d'ajuster facilement la distribution des navigateurs dans un scénario.

## <a name="adding-new-browsers-to-a-scenario"></a>Ajout de nouveaux navigateurs à un scénario

### <a name="to-add-new-browsers-to-a-scenario"></a>Pour ajouter de nouveaux navigateurs à un scénario

1.  Durant le processus de spécification de la combinaison de navigateurs pour un scénario, choisissez **Ajouter**.

     Une nouvelle entrée de navigateur est ajoutée à la grille.

    > [!NOTE]
    > Pour afficher la boîte de dialogue **Modifier la combinaison de navigateurs**, cliquez avec le bouton droit sur un scénario existant, puis choisissez **Modifier la combinaison de navigateurs**.

2.  Dans la colonne **Type de navigateur**, cliquez sur la flèche correspondant à la nouvelle entrée et choisissez le type de navigateur désiré.

3.  (Facultatif) Ajustez le contrôle de combinaison pour spécifier la distribution de test.

4.  Quand vous avez terminé d’ajouter des navigateurs, choisissez **OK**.

##  <a name="EditingTestMixSpecifyBrowserRemovingBrowserTypes"></a> Suppression de navigateurs d’un scénario

### <a name="to-remove-browsers-from-a-scenario"></a>Pour supprimer des navigateurs d'un scénario

1.  Ouvrez un test de charge.

2.  Cliquez avec le bouton droit sur le scénario à partir duquel vous souhaitez supprimer un navigateur, puis choisissez **Modifier la combinaison de navigateurs**.

     La boîte de dialogue **Modifier la combinaison de navigateurs** s’affiche.

3.  Sélectionnez le navigateur dans la grille, puis choisissez **Supprimer**.

4.  (Facultatif) Ajustez le contrôle de combinaison pour spécifier la distribution de test.

5.  Quand vous avez fini de supprimer des navigateurs, choisissez **OK**.

## <a name="about-the-mix-control"></a>À propos du contrôle de combinaison

 Le contrôle de combinaison vous permet d'ajuster le pourcentage de charge distribuée entre les tests, les types de navigateurs ou les types de réseaux dans un scénario de test de charge. Vous ajustez les valeurs en pourcentage en déplaçant des curseurs. L'ajustement de la combinaison de types de navigateur spécifie la probabilité qu'un utilisateur virtuel exécute un type de navigateur spécifique dans un scénario de test de charge.

 Lorsque vous déplacez un curseur, les valeurs en pourcentage de tous les éléments disponibles changent. Si plus de deux éléments sont disponibles, la charge que vous ajoutez ou supprimez est répartie de manière égale entre les autres éléments. Il est possible de modifier ce comportement. Si vous activez la case à cocher dans la colonne de verrouillage d'un élément particulier, vous verrouillez la valeur en pourcentage spécifiée pour cet élément. Ensuite, lorsque vous déplacez un curseur, la charge que vous ajoutez ou supprimez ne s'applique qu'aux éléments non verrouillés restants.

 Le bouton **Distribuer** permet d’allouer les valeurs en pourcentage de manière égale entre tous les éléments. Par exemple, si trois éléments sont disponibles et que vous choisissez **Distribuer**, les pourcentages sont 34, 33 et 33.

> [!WARNING]
> Le bouton **Distribuer** permet de remplacer les éléments verrouillés.

 Il est également possible de taper les valeurs en pourcentage directement dans la colonne **%** au lieu d’utiliser les curseurs. Si vous entrez directement une valeur en pourcentage, les autres éléments ne s'ajustent pas automatiquement.

> [!NOTE]
> Les curseurs sont désactivés quand le total n’atteint pas 100 % ou quand les valeurs en pourcentage entrées dans la colonne **%** sont des nombres décimaux.

 Lorsque vous entrez des valeurs en pourcentage manuellement, vous devez vous assurer que la somme de tous les éléments est 100 %. Lorsque vous enregistrez une combinaison, si la somme n'est pas égale à 100 %, vous serez invité à accepter les valeurs en pourcentage telles qu'elles sont ou à revenir en arrière pour les ajuster. Si vous choisissez de les accepter tels qu'ils sont, ils seront recalculés au prorata de 100 %.  Par exemple, si deux éléments sont disponibles et que vous les définissez manuellement à 80 % et 40 %, le premier élément aura pour valeur 66,67 % (80 divisé par 120) et le deuxième élément sera défini à 33,33 % (40 divisé par 120).

## <a name="see-also"></a>Voir aussi

- [Modification des scénarios de test de charge](../test/edit-load-test-scenarios.md)