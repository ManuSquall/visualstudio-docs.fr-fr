---
title: Créer un plug-in au niveau de la requête pour les tests de performances web
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- request-level plug-in, creating
- Web performance tests, requests
ms.assetid: d0b5b23c-7e94-4637-be6c-2620a5442d46
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b6e57f92a3f45983321a866f3524974ea99dba82
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589147"
---
# <a name="how-to-create-a-request-level-plug-in"></a>Guide pratique pour créer un plug-in de niveau requête

Les *requêtes* sont les instructions déclaratives qui constituent les tests de performances web. Les plug-ins de tests de performances de site Web vous permettent d'isoler et de réutiliser du code en dehors des principales instructions déclaratives de votre test de performances web. Vous pouvez créer des plug-ins et les ajouter à une requête individuelle aussi bien qu'au test de performances web qui la contient. Un *plug-in de requête* personnalisé permet d’appeler du code quand une requête particulière est exécutée dans un test de performances web.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Chaque plug-in de requête de test de performances web comporte une méthode PreRequest et une méthode PostRequest. Après avoir joint un plug-in de requête à une requête HTTP particulière, l'événement PreRequest est déclenché avant l'émission de la requête et l'événement PostRequest après la réception de la réponse.

Vous pouvez créer un plug-in de requête de test de performances web personnalisé en dérivant votre propre classe de la classe de base <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>.

En outre, vous pouvez utiliser des plug-ins de requête de test de performances web personnalisés avec des tests de performances web enregistrés. Les plug-ins de requête de test de performances web personnalisés vous permettent de minimiser le code à écrire pour arriver à mieux contrôler vos tests de performances web. Toutefois, vous pouvez également les utiliser avec des tests de performances web codés. Consultez [Générer et exécuter un test de performances web codé](../test/generate-and-run-a-coded-web-performance-test.md).

## <a name="to-create-a-request-level-plug-in"></a>Pour créer un plug-in de niveau demande

1. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur la solution, sélectionnez **Ajouter**, puis choisissez **Nouveau projet**.

2. Créez un projet de **Bibliothèque de classes**.

3. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le dossier **Références** de la nouvelle bibliothèque de classes, puis sélectionnez **Ajouter une référence**.

     La boîte de dialogue **Ajouter une référence** s’affiche.

4. Choisissez l’onglet **.NET**, faites défiler la liste vers le bas, sélectionnez **Microsoft.VisualStudio.QualityTools.WebTestFramework**, puis cliquez sur **OK**

     La référence à **Microsoft.VisualStudio.QualityTools.WebTestFramework** est ajoutée au dossier **Référence** dans **l’Explorateur de solutions**.

5. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le nœud supérieur du projet de test de performances web et de charge auquel vous souhaitez ajouter le plug-in du test de requête de test de performances web. Sélectionnez **Ajouter une référence**.

     La boîte de dialogue **Ajouter une référence** s’affiche.

6. Choisissez l’onglet **Projets**, sélectionnez le **Projet de bibliothèque de classes**, puis choisissez **OK**.

7. Dans **l’éditeur de code**, écrivez le code de votre plug-in. Commencez par créer une classe publique qui dérive de <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>.

8. Implémentez le code à l'intérieur d'un des gestionnaires d'événements <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin.PreRequest*> et <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin.PostRequest*>. Pour un exemple d'implémentation, reportez-vous à la section suivante.

9. Après avoir écrit le code, générez le nouveau projet.

10. Ouvrez le test de performances web auquel vous souhaitez ajouter le plug-in de requête.

11. Cliquez avec le bouton droit sur la requête à laquelle vous souhaitez ajouter le plug-in de requête, puis sélectionnez **Ajouter un plug-in de requête**.

     La boîte de dialogue **Ajouter un plug-in de requête de test web** s’affiche.

12. Sous **Sélectionner un plug-in**, sélectionnez votre nouveau plug-in.

13. Dans le volet **Propriétés du plug-in sélectionné**, définissez les valeurs initiales du plug-in à utiliser au moment de l’exécution.

    > [!NOTE]
    > Vous pouvez exposer autant de propriétés que vous souhaitez de vos plug-ins ; il suffit de les rendre publics, définissables et d'un type de base, tel qu'un entier, une valeur booléenne ou une chaîne. Vous pouvez également modifier ultérieurement les propriétés du plug-in de test de performances web dans la fenêtre Propriétés.

14. Cliquez sur **OK**.

     Le plug-in est ajouté au dossier **Plug-ins de requête**, qui est un dossier enfant de la requête HTTP.

    > [!WARNING]
    > Vous risquez de rencontrer l’erreur suivante si vous exécutez un test de performances web ou un test de charge qui utilise votre plug-in :
    >
    > **Échec de la requête : exception dans \<plug-in > événement : impossible de charger le fichier ou l’assembly'\<'nom du plug-in ". dll >, version =\<n. n. n. n >, culture = neutral, PublicKeyToken = null’ou l’une de ses dépendances. Le système ne peut pas trouver le fichier spécifié.**
    >
    > Cela se produit si vous effectuez des modifications du code dans l’un de vos plug-ins et si vous créez une autre version de la DLL **(Version=0.0.0.0)** . Toutefois, le plug-in fait toujours référence à la version du plug-in d’origine. Pour résoudre ce problème, procédez comme suit :
    >
    > 1. Dans le projet de test de performances web et de charge, un message d'avertissement s'affiche dans les références. Supprimez et rajoutez la référence à la DLL de votre plug-in.
    > 2. Supprimez le plug-in de votre test ou de l'emplacement approprié, puis rajoutez-le.

## <a name="example"></a>Exemple

Vous pouvez utiliser le code suivant pour créer un plug-in de test de performances web personnalisé qui affiche deux boîtes de dialogue. La première boîte de dialogue affiche l’URL associée à la requête à laquelle vous joignez le complément de requête. La deuxième boîte de dialogue affiche le nom de l'ordinateur de l'agent.

> [!NOTE]
> Le code suivant requiert l'ajout d'une référence à System.Windows.Forms.

```csharp
using System;
using System.Collections.Generic;
using System.Windows.Forms;
using Microsoft.VisualStudio.TestTools.WebTesting;

namespace RequestPluginNamespace
{
    public class MyWebRequestPlugin : WebTestRequestPlugin
    {
        public override void PostRequest(object sender, PostRequestEventArgs e)
        {
            MessageBox.Show(e.WebTest.Context.AgentName);
        }
        public override void PreRequest(object sender, PreRequestEventArgs e)
        {
            MessageBox.Show(e.Request.Url);
        }
    }
}
```

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- [Créer du code et des plug-ins personnalisés pour les tests de charge](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Coder une règle d’extraction personnalisée pour un test de performances web](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Coder une règle de validation personnalisée pour un test de performances web](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Guide pratique pour créer un plug-in de test de charge](../test/how-to-create-a-load-test-plug-in.md)
- [Générer et exécuter un test de performances web codé](../test/generate-and-run-a-coded-web-performance-test.md)
