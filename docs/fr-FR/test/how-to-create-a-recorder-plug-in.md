---
title: Créer un plug-in d’enregistreur pour les tests de performances web dans Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, recorder plug-in
ms.assetid: 6fe13be1-aeb5-4927-9bff-35950e194da9
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 008275d4e0ff094c7933b4e0bae89055acd4bf8e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-recorder-plug-in"></a>Comment : créer un plug-in d'enregistreur

Le <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin> permet de modifier un test de performances de site Web enregistré. La modification se produit une fois que vous choisissez **Arrêter** dans la barre d’outils de l’enregistreur de test de performances web, mais avant l’enregistrement et la présentation du test dans l’éditeur de tests de performances web.

Un plug-in d’enregistreur vous permet d’effectuer votre propre corrélation personnalisée sur des paramètres dynamiques. Avec la fonctionnalité de corrélation intégrée, les tests de performances web détectent les paramètres dynamiques dans l’enregistrement web une fois l’opération terminée, ou quand vous utilisez l’option **Promouvoir les paramètres dynamiques en paramètres de test web** sur la barre d’outils de l’éditeur de tests de performances web. Toutefois, la fonctionnalité de détection intégrée ne trouve pas toujours tous les paramètres dynamiques. Par exemple, il ne trouve pas d'ID de session, qui obtient généralement sa valeur modifiée entre 5 à 30 minutes. Par conséquent, vous devez exécuter le processus de corrélation manuellement.

Le <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin> permet d'écrire le code de votre plug-in personnalisé. Ce plug-in peut exécuter une corrélation ou modifier le test de performances de site Web de plusieurs manières avant d'être enregistré et présenté dans l'éditeur de tests de performances de site Web. Par conséquent, si vous déterminez qu'une variable dynamique spécifique doit être mise en corrélation pour de nombreux enregistrements, vous pouvez automatiser le processus.

Vous pouvez également utiliser un plug-in d’enregistreur pour ajouter des règles d’extraction et de validation, ajouter des paramètres de contexte ou convertir les commentaires en transactions dans un test de performances de site Web.

Les procédures suivantes décrivent le mode de création du code rudimentaire pour un plug-in d'enregistreur, déployez le plug-in et exécutez-le. L'exemple de code qui suit les procédures montre comment utiliser Visual C# pour créer un plug-in d'enregistreur de la corrélation avec des paramètres dynamiques personnalisés.

## <a name="creating-a-recorder-plug-in"></a>Création d'un plug-in d'enregistreur

### <a name="to-create-a-recorder-plug-in"></a>Pour créer un plug-in d'enregistreur

1.  Ouvrez une solution qui contient le projet de test de performances de site Web et de charge avec le test de performances de site Web pour lequel vous souhaitez créer un plug-in d'enregistreur.

2.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur la solution, sélectionnez **Ajouter**, puis choisissez **Nouveau projet**.

     La boîte de dialogue **Ajouter un nouveau projet** s’affiche.

3.  Sous **Modèles installés**, sélectionnez **Visual C#**.

4.  Dans la liste des modèles, sélectionnez **Bibliothèque de classes**.

5.  Dans la zone de texte **Nom**, tapez un nom pour le plug-in d’enregistreur.

     La nouvelle bibliothèque de classes est ajouté à l'Explorateur de solutions et la nouvelle classe s'ouvre dans l'éditeur de code.

6.  Dans l’Explorateur de solutions, dans le dossier de projet de la nouvelle bibliothèque de classes, cliquez avec le bouton droit sur le dossier **Références** et sélectionnez **Ajouter une référence**.

    > [!TIP]
    > **RecorderPlugins** est un exemple de dossier de projet de nouvelle bibliothèque de classes.

     La boîte de dialogue **Ajouter une référence** s’affiche.

7.  Sélectionnez l’onglet **.NET**.

8.  Faites défiler la liste vers le bas et sélectionnez **Microsoft.VisualStudio.QualityTools.WebTestFramework**, puis choisissez **OK**.

     **Microsoft.VisualStudio.QualityTools.WebTestFramework** est ajouté dans le dossier **Références** dans l’Explorateur de solutions.

9. Écrivez le code de votre plug-in d'enregistreur. Commencez par créer une classe publique qui dérive de <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin>.

10. Remplacez la méthode <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*>.

    ```csharp
    public class Class1 : WebTestRecorderPlugin
        {
            public override void PostWebTestRecording(object sender, PostWebTestRecordingEventArgs e)
            {
                base.PostWebTestRecording(sender, e);
            }
        }
    ```

     Les arguments de l'événement fournissent deux objets à utiliser : le résultat enregistré et le test de performances de site Web enregistré. Cela vous permettra d'itérer au sein du résultat à la recherche de certaines valeurs, puis d'accéder à la même requête dans le test de performances de site Web pour effectuer des modifications. Vous pouvez également modifier juste le test de performances de site Web pour ajouter un paramètre de contexte ou pour paramétrer des parties de l'URL.

    > [!NOTE]
    > Si vous modifiez le test de performances de site Web, vous devez également définir la propriété <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestRecordingEventArgs.RecordedWebTestModified*> avec la valeur True : `e.RecordedWebTestModified = true;`

11. Ajoutez d'autres lignes de code en fonction de la nature des opérations à exécuter par le plug-in d'enregistreur à l'issue de l'enregistrement Web. Par exemple, vous pouvez ajouter le code pour gérer la corrélation personnalisée comme l'illustre l'exemple ci-dessous. Vous pouvez également créer un plug-in d’enregistreur pour notamment convertir les commentaires en transactions ou ajouter des règles de validation au test de performances de site Web.

12. Dans le menu **Générer**, choisissez Générer \<nom du projet de la bibliothèque de classes>.

13. Ensuite, vous devez déployer le plug-in d'enregistreur pour l'enregistrer avec Visual Studio.

### <a name="deploy-the-recorder-plug-in"></a>Déployer le plug-in d'enregistreur

Après avoir compilé le plug-in d'enregistreur, vous devrez placer la DLL créée dans un des deux emplacements :

-   %ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies\WebTestPlugins

-   %USERPROFILE%\My Documents\Visual Studio \<*version*>\WebTestPlugins

> [!WARNING]
> Après avoir copié le plug-in d'enregistreur dans l'un des deux emplacements, vous devez redémarrer Visual Studio pour enregistrer le plug-in d'enregistreur.

### <a name="to-execute-the-recorder-plug-in"></a>Pour exécuter le plug-in d'enregistreur

1.  Créer un test de performances de site web.

     La boîte de dialogue **Activer WebTestRecordPlugins** s’affiche.

2.  Activez la case à cocher du plug-in d'enregistreur et choisissez OK.

     À l'issue de l'enregistrement du test de performances de site Web, le nouveau plug-in d'enregistreur sera exécuté.

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

Cet exemple montre comment créer un plug-in d'enregistreur pour le test de performances de site Web personnalisé afin d'exécuter la corrélation personnalisée des paramètres dynamiques.

> [!NOTE]
> Une liste complète de l'exemple de code se trouve à la fin de cette rubrique.

 **Revue de l’exemple de code**

## <a name="iterate-through-the-result-to-find-first-page-with-reportsession"></a>Effectue une itération au sein du résultat pour rechercher la première page avec ReportSession

Cette partie de l'exemple de code effectue une itération au sein de chaque objet enregistré et recherche le corps de la réponse de ReportSession.

```csharp
foreach (WebTestResultUnit unit in e.RecordedWebTestResult.Children)
 {
     WebTestResultPage page = unit as WebTestResultPage;
     if (page != null)
     {
         if (!foundId)
         {
             int indexOfReportSession = page.RequestResult.Response.BodyString.IndexOf("ReportSession");
             if (indexOfReportSession > -1)
             {
```

## <a name="add-an-extraction-rule"></a>Ajouter une règle d'extraction

Maintenant qu'une réponse a été trouvée, vous devez ajouter une règle d'extraction. Cette partie de l'exemple de code crée la règle d'extraction à l'aide de la classe <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRuleReference>, puis recherche la requête correcte dans le test de performances de site Web pour y ajouter la règle d'extraction. Chaque objet résultat a une nouvelle propriété ajoutée nommée DeclarativeWebTestItemId qui est utilisée dans le code pour obtenir la requête appropriée du test de performances de site Web.

```csharp
ExtractionRuleReference ruleReference = new ExtractionRuleReference();
     ruleReference.Type = typeof(ExtractText);
     ruleReference.ContextParameterName = "SessionId";
     ruleReference.Properties.Add(new PluginOrRuleProperty("EndsWith", "&ControlID="));
     ruleReference.Properties.Add(new PluginOrRuleProperty("HtmlDecode", "True"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("IgnoreCase", "True"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("Index", "0"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("Required", "True"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("StartsWith", "ReportSession="));
     ruleReference.Properties.Add(new PluginOrRuleProperty("UseRegularExpression", "False"));

     WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
     if (requestInWebTest != null)
     {
         requestInWebTest.ExtractionRuleReferences.Add(ruleReference);
         e.RecordedWebTestModified = true;
     }
```

## <a name="replace-query-string-parameters"></a>Remplacer les paramètres de chaîne de requête

Maintenant, le code recherche tous les paramètres de chaîne de requête dont le nom ReportSession et remplacez la valeur par {{SessionId}} comme indiqué dans cette partie de l'exemple de code :

```csharp
WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
if (requestInWebTest != null)
{
    foreach (QueryStringParameter param in requestInWebTest.QueryStringParameters)
    {
         if (param.Name.Equals("ReportSession"))
         {
             param.Value = "{{SessionId}}";
         }
     }
 }
```

```csharp
using System.ComponentModel;
using Microsoft.VisualStudio.TestTools.WebTesting;
using Microsoft.VisualStudio.TestTools.WebTesting.Rules;

namespace RecorderPlugin
{
    [DisplayName("Correlate ReportSession")]
    [Description("Adds extraction rule for Report Session and binds this to querystring parameters that use ReportSession")]
    public class CorrelateSessionId : WebTestRecorderPlugin
    {
        public override void PostWebTestRecording(object sender, PostWebTestRecordingEventArgs e)
        {
            //first find the session id
            bool foundId = false;
            foreach (WebTestResultUnit unit in e.RecordedWebTestResult.Children)
            {
                WebTestResultPage page = unit as WebTestResultPage;
                if (page != null)
                {
                    if (!foundId)
                    {
                        int indexOfReportSession = page.RequestResult.Response.BodyString.IndexOf("ReportSession");
                        if (indexOfReportSession > -1)
                        {
                            //add an extraction rule to this request
                            // Get the corresponding request in the Declarative Web performance test
                            ExtractionRuleReference ruleReference = new ExtractionRuleReference();

                            ruleReference.Type = typeof(ExtractText);
                            ruleReference.ContextParameterName = "SessionId";
                            ruleReference.Properties.Add(new PluginOrRuleProperty("EndsWith", "&ControlID="));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("HtmlDecode", "True"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("IgnoreCase", "True"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("Index", "0"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("Required", "True"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("StartsWith", "ReportSession="));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("UseRegularExpression", "False"));

                            WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
                            if (requestInWebTest != null)
                            {
                                requestInWebTest.ExtractionRuleReferences.Add(ruleReference);
                                e.RecordedWebTestModified = true;
                            }
                            foundId = true;

                        }
                    }
                    else
                    {
                        //now update query string parameters
                        WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
                        if (requestInWebTest != null)
                        {
                            foreach (QueryStringParameter param in requestInWebTest.QueryStringParameters)
                            {
                                if (param.Name.Equals("ReportSession"))
                                {
                                    param.Value = "{{SessionId}}";
                                }
                            }
                        }
                    }
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRuleReference>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*>
- [Créer du code et des plug-ins personnalisés pour les tests de charge](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Générer et exécuter un test de performances web codé](../test/generate-and-run-a-coded-web-performance-test.md)