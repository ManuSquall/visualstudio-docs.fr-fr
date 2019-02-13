---
title: Créer un plug-in de test de performances web
ms.date: 10/03/2016
ms.topic: conceptual
f1_keywords:
- vs.test.web.webtestplugin
helpviewer_keywords:
- Web performance tests, creating plug-ins
- plug-ins, creating in Web performance tests
ms.assetid: a612f2d2-9806-477d-a126-12842f07da6e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6a9b5ec7b0a4231297925ab8b487ec3f529ddaef
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55955100"
---
# <a name="how-to-create-a-web-performance-test-plug-in"></a>Procédure : créer un plug-in de test de performances web

Les plug-ins de tests de performances web vous permettent d'isoler et de réutiliser du code en dehors des principales instructions déclaratives de votre test de performances web. Un plug-in de test de performancesweb personnalisé permet d'appeler du code durant l'exécution du test de performances web. Le plug-in de test de performances web est exécuté une seule fois pour chaque itération de test. De plus, si vous substituez les méthodes PreRequest ou PostRequest dans le plug-in de test, ces plug-ins de requête s'exécuteront avant ou après chaque requête, respectivement.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Vous pouvez créer un plug-in de test de performances web personnalisé en dérivant votre propre classe de la classe de base <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>.

Vous pouvez utiliser des plug-ins de test de performances web personnalisés avec les tests de performances web que vous avez enregistrés, ce qui vous permet d'écrire une quantité minimale de code pour obtenir un niveau supérieur de contrôle sur vos tests de performances web. Toutefois, vous pouvez également les utiliser avec des tests de performances web codés. Pour plus d’informations, consultez [Générer et exécuter un test de performances web codé](../test/generate-and-run-a-coded-web-performance-test.md).

> [!NOTE]
> Vous pouvez également créer des plug-ins de test de charge. Consultez [Guide pratique pour créer un plug-in de test de charge](../test/how-to-create-a-load-test-plug-in.md).

## <a name="to-create-a-custom-web-performance-test-plug-in"></a>Pour créer un plug-in de test de performances de site web

1.  Ouvrez un projet de test de performances web et de charge qui contient un test de performances web.

2.  Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur la solution, sélectionnez **Ajouter**, puis choisissez **Nouveau projet**.

     La boîte de dialogue **Ajouter un nouveau projet** s’affiche.

3.  Sous **Modèles installés**, sélectionnez **Visual C#**.

4.  Dans la liste des modèles, sélectionnez **Bibliothèque de classes**.

5.  Dans la zone de texte **Nom**, tapez le nom de votre classe.

6.  Cliquez sur **OK**.

7.  Le nouveau projet de bibliothèque de classes est ajouté à **l’Explorateur de solutions** et la nouvelle classe s’affiche dans **l’éditeur de code**.

8.  Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le dossier **Références** de la nouvelle bibliothèque de classes, puis sélectionnez **Ajouter une référence**.

9. La boîte de dialogue **Ajouter une référence** s’affiche.

10. Choisissez l’onglet **.NET**, faites défiler la liste vers le bas, puis sélectionnez **Microsoft.VisualStudio.QualityTools.WebTestFramework**

11. Cliquez sur **OK**.

     La référence à **Microsoft.VisualStudio.QualityTools.WebTestFramework** est ajoutée au dossier **Référence** dans **l’Explorateur de solutions**.

12. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le nœud supérieur du projet de test de performances web et de charge qui contient le test de charge auquel vous souhaitez ajouter le plug-in du test de performances web, puis sélectionnez **Ajouter une référence**.

13. La boîte de dialogue **Ajouter une référence** s’affiche.

14. Choisissez l’onglet **Projets**, puis sélectionnez le **Projet de bibliothèque de classes**.

15. Cliquez sur **OK**.

16. Dans **l’éditeur de code**, écrivez le code de votre plug-in. Commencez par créer une classe publique qui dérive de <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>.

17. Implémentez le code dans un ou plusieurs gestionnaires d'événements. Pour un exemple d'implémentation, reportez-vous à la section suivante.

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestRecordingEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PreRequestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostRequestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PrePageEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostPageEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PreTransactionEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostTransactionEventArgs>

18. Après avoir écrit le code, générez le nouveau projet.

19. Ouvrez un test de performances web.

20. Pour ajouter le plug-in de test de performances web, choisissez **Ajouter un plug-in de test Web**dans la barre d’outils.

     La boîte de dialogue **Ajouter un plug-in de test web** s’affiche.

21. Sous **Sélectionner un plug-in**, sélectionnez votre classe de plug-in de test de performances web.

22. Dans le volet **Propriétés du plug-in sélectionné**, définissez les valeurs initiales du plug-in à utiliser au moment de l’exécution.

    > [!NOTE]
    > Vous pouvez exposer autant de propriétés que vous souhaitez de vos plug-ins ; il suffit de les rendre publics, définissables et d'un type de base, tel qu'un entier, une valeur booléenne ou une chaîne. Vous pouvez également modifier ultérieurement les propriétés du plug-in de test de performances web dans la fenêtre Propriétés.

23. Cliquez sur **OK**.

     Le plug-in est ajouté au dossier **Plug-ins de test web**.

    > [!WARNING]
    > Vous pouvez obtenir une erreur semblable au cas suivant lorsque vous exécutez un test de performances web ou un test de charge qui utilise votre plug-in :
    >
    > **Échec de la requête : Exception dans le \<plug-in> événement : Impossible de charger le fichier ou l’assembly '\<"Nom du plug-in".dll>, Version=\<n.n.n.n>, Culture=neutral, PublicKeyToken=null' ou l’une de ses dépendances. Le système ne parvient pas à localiser le fichier spécifié.**
    >
    > Cela se produit si vous effectuez des modifications du code dans l’un de vos plug-ins et si vous créez une autre version de la DLL **(Version=0.0.0.0)**. Toutefois, le plug-in fait toujours référence à la version du plug-in d’origine. Pour résoudre ce problème, procédez comme suit :
    >
    > 1.  Dans le projet de test de performances web et de charge, un message d’avertissement s’affiche dans les références. Supprimez et rajoutez la référence à la DLL de votre plug-in.
    > 2.  Supprimez le plug-in de votre test ou de l'emplacement approprié, puis rajoutez-le.

## <a name="example"></a>Exemple

Le code suivant crée un plug-in de test de performances web personnalisé qui ajoute un élément au <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestContext> qui représente l'itération de test.

Après l’exécution du test de performances web, à l’aide de ce plug-in, vous pouvez voir l’élément ajouté nommé **TestIteratnionNumber** sous l’onglet **Contexte** de l’**Afficheur de résultats de test de performances web**.

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
- [Créer du code et des plug-ins personnalisés pour les tests de charge](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Guide pratique pour créer un plug-in au niveau de la requête](../test/how-to-create-a-request-level-plug-in.md)
- [Coder une règle d’extraction personnalisée pour un test de performances web](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Coder une règle de validation personnalisée pour un test de performances web](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Guide pratique pour créer un plug-in de test de charge](../test/how-to-create-a-load-test-plug-in.md)
- [Générer et exécuter un test de performances web codé](../test/generate-and-run-a-coded-web-performance-test.md)