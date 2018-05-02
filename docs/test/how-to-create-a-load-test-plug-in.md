---
title: Créer un plug-in de test de charge dans Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.loadtestplugin
helpviewer_keywords:
- code, load tests
- plug-ins, load test
- load tests, plug-ins
ms.assetid: 27806972-1b15-4388-833d-6d0632816f1f
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 482336bca7c177b3c4fdcb0f16faf7ea96d6c34b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-load-test-plug-in"></a>Comment : créer un plug-in de test de charge

Vous pouvez créer un plug-in de test de charge pour exécuter du code à différents stades de l'exécution du test de charge. Vous pouvez créer un plug-in pour développer ou modifier la fonctionnalité intégrée du test de charge. Par exemple, vous pouvez coder un plug-in de test de charge pour définir ou modifier le modèle de test de charge pendant l'exécution du test de charge. Pour cela, vous devez créer une classe qui hérite de l'interface de <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>. Cette classe doit implémenter la méthode <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin.Initialize*> de cette interface. Pour plus d'informations, consultez <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>.

> [!NOTE]
> Vous pouvez également créer des plug-ins pour les tests de performances de site web. Pour plus d’informations, consultez [Guide pratique pour créer un plug-in de test de performances web](../test/how-to-create-a-web-performance-test-plug-in.md).

## <a name="to-create-a-load-test-plug-in-by-using-visual-c"></a>Pour créer un plug-in de test de charge à l'aide de Visual C#

1.  Ouvrez un projet de test de performances de site web et de charge qui contient un test de performances de site web.

2.  Ajoutez un test de charge au projet de test et configurez-le pour exécuter un test de performances de site Web.

     Pour plus d’informations, consultez [Guide pratique pour créer un projet de test de charge](../test/quickstart-create-a-load-test-project.md).

3.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur la solution et sélectionnez **Ajouter**, puis choisissez **Nouveau projet**.

     La boîte de dialogue **Ajouter un nouveau projet** s’affiche.

4.  Sous **Modèles installés**, sélectionnez **Visual C#**.

5.  Dans la liste des modèles, sélectionnez **Bibliothèque de classes**.

6.  Dans la zone de texte **Nom**, tapez le nom de votre classe.

7.  Cliquez sur **OK**.

8.  Le nouveau projet de bibliothèque de classes est ajouté à l'Explorateur de solutions et la nouvelle classe s'affiche dans l'éditeur de code.

9. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le dossier **Références** de la nouvelle bibliothèque de classes, puis sélectionnez **Ajouter une référence**.

10. La boîte de dialogue **Ajouter une référence** s’affiche.

11. Choisissez l’onglet **.NET**, faites défiler la page, puis sélectionnez **Microsoft.VisualStudio.QualityTools.LoadTestFramework**.

12. Cliquez sur **OK**.

     La référence à **Microsoft.VisualStudio.QualityTools.LoadTestFramework** est ajoutée au dossier **Référence** dans l’Explorateur de solutions.

13. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le nœud supérieur du projet de test de performances web et de charge qui contient le test de charge auquel vous souhaitez ajouter le plug-in de test de charge, puis sélectionnez **Ajouter une référence**.

14. La boîte de dialogue **Ajouter une référence** s’affiche.

15. Choisissez l’onglet **Projets**, puis sélectionnez le projet de bibliothèque de classes.

16. Cliquez sur **OK**.

17. Dans l'éditeur de code, ajoutez une instruction `using` pour l'espace de noms <xref:Microsoft.VisualStudio.TestTools.LoadTesting>.

18. Implémentez l'interface <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> pour la classe créée dans le projet de bibliothèque de classes. Pour un exemple d'implémentation, reportez-vous à la section suivante.

19. Après avoir écrit le code, générez le nouveau projet.

20. Cliquez avec le bouton droit sur le nœud supérieur du test de charge, puis choisissez **Ajouter un plug-in de test de charge**.

     La boîte de dialogue **Ajouter un plug-in de test de charge** s’affiche.

21. Sous **Sélectionner un plug-in**, sélectionnez votre classe du plug-in du test de charge.

22. Dans le volet **Propriétés du plug-in sélectionné**, définissez les valeurs initiales du plug-in à utiliser au moment de l’exécution.

    > [!NOTE]
    > Vous pouvez exposer autant de propriétés que vous souhaitez de vos plug-ins ; il suffit de les rendre publics, définissables et d'un type de base, tel qu'un entier, une valeur booléenne ou une chaîne. Vous pouvez également modifier ultérieurement les propriétés du plug-in de test de performances de site web dans la fenêtre Propriétés.

23. Cliquez sur **OK**.

     Le plug-in est ajouté au dossier **Plug-ins de test de charge**.

    > [!WARNING]
    > Vous pouvez obtenir une erreur semblable au cas suivant lorsque vous exécutez un test de performances de site web ou un test de charge qui utilise votre plug-in :
    >
    > **Échec de la requête : exception dans le \<plug-in> événement : Impossible de charger le fichier ou l’assembly '\<"Nom du plug-in".dll>, Version=\<n.n.n.n>, Culture=neutral, PublicKeyToken=null' ou l’une de ses dépendances. Le système ne parvient pas à localiser le fichier spécifié.**
    >
    > Cela se produit si vous effectuez des modifications du code dans l’un de vos plug-ins et si vous créez une autre version de la DLL **(Version=0.0.0.0)**. Toutefois, le plug-in fait toujours référence à la version du plug-in d’origine. Pour résoudre ce problème, procédez comme suit :
    >
    > 1.  Dans votre projet de test de performances de site web et de charge, un message d'avertissement s'affiche dans les références. Supprimez et rajoutez la référence à la DLL de votre plug-in.
    > 2.  Supprimez le plug-in de votre test ou de l'emplacement approprié, puis rajoutez-le.

## <a name="example"></a>Exemple

Le code suivant illustre un plug-in de test de charge qui exécute du code personnalisé suite à un événement LoadTestFinished. Si ce code est exécuté sur un agent de test sur un ordinateur distant et si l'agent et le contrôleur de test n'ont pas de service SMTP localhost, le test de charge reste à l'état "En cours" car une boîte de message est ouverte.

> [!NOTE]
> Le code suivant requiert l'ajout d'une référence à System.Windows.Forms.


```csharp
using System;
using Microsoft.VisualStudio.TestTools.LoadTesting;
using System.Net.Mail;
using System.Windows.Forms;

namespace LoadTestPluginTest
{
    public class MyLoadTestPlugin : ILoadTestPlugin
    {
        LoadTest myLoadTest;

        public void Initialize(LoadTest loadTest)
        {
            myLoadTest = loadTest;
            myLoadTest.LoadTestFinished += new
                EventHandler(myLoadTest_LoadTestFinished);
        }

        void myLoadTest_LoadTestFinished(object sender, EventArgs e)
        {
            try
            {
                // place custom code here
                MailAddress MyAddress = new MailAddress("someone@example.com");
                MailMessage MyMail = new MailMessage(MyAddress, MyAddress);
                MyMail.Subject = "Load Test Finished -- Admin Email";
                MyMail.Body = myLoadTest..Name + " has finished.";

                SmtpClient MySmtpClient = new SmtpClient("localhost");
                MySmtpClient.Send(MyMail);
            }

            catch (SmtpException ex)
            {
                MessageBox.Show(ex.InnerException.Message +
                    ".\r\nMake sure you have a valid SMTP.", "LoadTestPlugin", MessageBoxButtons.OK, MessageBoxIcon.Warning, MessageBoxDefaultButton.Button1);
            }
        }
    }
}
```

Huit événements sont associés à un test de charge et peuvent être gérés dans le plug-in de test de charge pour exécuter du code personnalisé avec le test de charge. Voici une liste des événements qui procurent un accès à différentes périodes de la série de tests de charge :

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestStarting>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestFinished>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestWarmupComplete>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.TestStarting>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.TestFinished>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.ThresholdExceeded>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.Heartbeat>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestAborted>

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>
- [Créer du code et des plug-ins personnalisés pour les tests de charge](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Guide pratique pour créer un plug-in de test des performances web](../test/how-to-create-a-web-performance-test-plug-in.md)