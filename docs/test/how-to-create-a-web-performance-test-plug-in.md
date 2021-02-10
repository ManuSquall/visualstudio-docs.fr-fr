---
title: Créer un plug-in de test de performances web
description: Découvrez comment les plug-ins de test de performances de site Web vous permettent de réutiliser du code en dehors des instructions déclaratives principales dans votre test de performances de site Web.
ms.custom: SEO-VS-2020
ms.date: 10/03/2016
ms.topic: how-to
f1_keywords:
- vs.test.web.webtestplugin
helpviewer_keywords:
- Web performance tests, creating plug-ins
- plug-ins, creating in Web performance tests
ms.assetid: a612f2d2-9806-477d-a126-12842f07da6e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 758f57d3b934298ef397984b174fbf2c38d93d1b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952549"
---
# <a name="how-to-create-a-web-performance-test-plug-in"></a>Guide pratique pour créer un plug-in de test de performances web

Les plug-ins de tests de performances web vous permettent d'isoler et de réutiliser du code en dehors des principales instructions déclaratives de votre test de performances web. Un plug-in de test de performancesweb personnalisé permet d'appeler du code durant l'exécution du test de performances web. Le plug-in de test de performances web est exécuté une seule fois pour chaque itération de test. De plus, si vous substituez les méthodes PreRequest ou PostRequest dans le plug-in de test, ces plug-ins de requête s'exécuteront avant ou après chaque requête, respectivement.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Vous pouvez créer un plug-in de test de performances web personnalisé en dérivant votre propre classe de la classe de base <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>.

Vous pouvez utiliser des plug-ins de test de performances web personnalisés avec les tests de performances web que vous avez enregistrés, ce qui vous permet d'écrire une quantité minimale de code pour obtenir un niveau supérieur de contrôle sur vos tests de performances web. Toutefois, vous pouvez également les utiliser avec des tests de performances web codés. Pour plus d’informations, consultez [Générer et exécuter un test de performances web codé](../test/generate-and-run-a-coded-web-performance-test.md).

> [!NOTE]
> Vous pouvez également créer des plug-ins de test de charge. Consultez [Comment : créer un plug-in de test de charge](../test/how-to-create-a-load-test-plug-in.md).

## <a name="to-create-a-custom-web-performance-test-plug-in"></a>Pour créer un plug-in de test de performances de site web

1. Ouvrez un projet de test de performances web et de charge contenant un test de performances web.

2. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur la solution et sélectionnez **Ajouter** , puis choisissez **nouveau projet**.

3. Créez un projet de **Bibliothèque de classes**.

   Le nouveau projet de bibliothèque de classes est ajouté à **l’Explorateur de solutions** et la nouvelle classe s’affiche dans **l’éditeur de code**.

4. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le dossier **références** dans la nouvelle bibliothèque de classes, puis sélectionnez **Ajouter une référence**.

   La boîte de dialogue **Ajouter une référence** s’affiche.

5. Choisissez l’onglet **.NET**, faites défiler la liste vers le bas, puis sélectionnez **Microsoft.VisualStudio.QualityTools.WebTestFramework**

6. Choisissez **OK**.

     La référence à **Microsoft. VisualStudio. QualityTools. WebTestFramework** est ajoutée au dossier de **référence** dans **Explorateur de solutions**.

7. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud supérieur du projet de test de performances de site Web et de charge qui contient le test de charge auquel vous souhaitez ajouter le plug-in de test de performances de site Web et sélectionnez **Ajouter une référence**.

8. La **boîte de dialogue Ajouter une référence s’affiche**.

9. Choisissez l’onglet **projets** et sélectionnez le **projet de bibliothèque de classes**.

10. Choisissez **OK**.

11. Dans **l’éditeur de code**, écrivez le code de votre plug-in. Commencez par créer une classe publique qui dérive de <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>.

12. Implémentez le code dans un ou plusieurs gestionnaires d'événements. Pour un exemple d'implémentation, reportez-vous à la section suivante.

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestRecordingEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PreRequestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostRequestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PrePageEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostPageEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PreTransactionEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostTransactionEventArgs>

13. Après avoir écrit le code, générez le nouveau projet.

14. Ouvrez un test de performances web.

15. Pour ajouter le plug-in de test de performances de site Web, choisissez **Ajouter un plug-in de test Web** dans la barre d’outils.

     La boîte de dialogue **Ajouter un plug-in de test web** s’affiche.

16. Sous **Sélectionner un plug-** in, sélectionnez votre classe de plug-in de test de performances de site Web.

17. Dans le volet **Propriétés du plug-in sélectionné**, définissez les valeurs initiales du plug-in à utiliser au moment de l’exécution.

    > [!NOTE]
    > Vous pouvez exposer autant de propriétés que vous souhaitez de vos plug-ins ; il suffit de les rendre publics, définissables et d'un type de base, tel qu'un entier, une valeur booléenne ou une chaîne. Vous pouvez également modifier ultérieurement les propriétés du plug-in de test de performances web dans la fenêtre Propriétés.

18. Choisissez **OK**.

     Le plug-in est ajouté au dossier **Plug-ins de test web**.

    > [!WARNING]
    > Vous risquez de rencontrer l’erreur suivante si vous exécutez un test de performances web ou un test de charge qui utilise votre plug-in :
    >
    > **Échec de la requête : exception dans l' \<plug-in> événement : impossible de charger le fichier ou l’assembly' \<"Plug-in name".dll file> , version = \<n.n.n.n> , culture = neutral, PublicKeyToken = null’ou l’une de ses dépendances. Le système ne peut pas trouver le fichier spécifié.**
    >
    > Cela se produit si vous effectuez des modifications du code dans l’un de vos plug-ins et si vous créez une autre version de la DLL **(Version=0.0.0.0)**. Toutefois, le plug-in fait toujours référence à la version du plug-in d’origine. Pour résoudre ce problème, procédez comme suit :
    >
    > 1. Dans le projet de test de performances web et de charge, un message d'avertissement s'affiche dans les références. Supprimez et rajoutez la référence à la DLL de votre plug-in.
    > 2. Supprimez le plug-in de votre test ou de l'emplacement approprié, puis rajoutez-le.

## <a name="example"></a>Exemple

Le code suivant crée un plug-in de test de performances web personnalisé qui ajoute un élément au <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestContext> qui représente l'itération de test.

Après avoir exécuté le test de performances de site Web, à l’aide de ce plug-in, vous pouvez voir l’élément ajouté nommé **testiteratnionnumber sous** dans l’onglet **contexte** de l' **Afficheur des résultats des performances de site Web**.

```csharp
using System;
using System.Collections.Generic;
using System.Text;
using System.ComponentModel;
using Microsoft.VisualStudio.TestTools.WebTesting;

namespace SampleRules
{
    [Description("This plugin can be used to set the ParseDependentsRequests property for each request")]
    public class SampleWebTestPlugin : WebTestPlugin
    {
        private bool m_parseDependents = true;

        public override void PreWebTest(object sender, PreWebTestEventArgs e)
        {
            // TODO: Add code to execute before the test.
        }

        public override void PostWebTest(object sender, PostWebTestEventArgs e)
        {
            // TODO: Add code to execute after the test.
        }

        public override void PreRequest(object sender, PreRequestEventArgs e)
        {
            // Code to execute before each request.
            // Set the ParseDependentsRequests value on the request
            e.Request.ParseDependentRequests = m_parseDependents;
        }

        // Properties for the plugin.
        [DefaultValue(true)]
        [Description("All requests will have their ParseDependentsRequests property set to this value")]
        public bool ParseDependents
        {
            get
            {
                return m_parseDependents;
            }
            set
            {
                m_parseDependents = value;
            }
        }
    }
}
```

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- [Créer un code et des plug-ins personnalisés pour les tests de charge](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Comment : créer un plug-in de niveau demande](../test/how-to-create-a-request-level-plug-in.md)
- [Coder une règle d’extraction personnalisée pour un test de performances web](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Coder une règle de validation personnalisée pour un test de performances web](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Guide pratique pour créer un plug-in de test de charge](../test/how-to-create-a-load-test-plug-in.md)
- [Générer et exécuter un test de performances de site Web codé](../test/generate-and-run-a-coded-web-performance-test.md)
