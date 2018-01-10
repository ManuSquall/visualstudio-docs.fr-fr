---
title: "Test d’une grande application avec plusieurs mappages d’IU | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- coded UI tests, multiple UI maps
- coded UI tests, for large applications
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: ca9114dfe601f523878749593a213b36465bd0a7
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2018
---
# <a name="testing-a-large-application-with-multiple-ui-maps"></a>Test d'une grande application avec plusieurs mappages d'IU
Cette rubrique explique comment utiliser des tests codés de l'interface utilisateur quand vous testez une grande application à l'aide de plusieurs mappages d'interface utilisateur.  
  
 **Spécifications**  
  
-   Visual Studio Enterprise  
  
 Quand vous créez un test codé de l’interface utilisateur, le framework de test de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] génère du code pour le test par défaut dans une classe <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>. Pour plus d’informations sur l’enregistrement des tests codés de l’interface utilisateur, consultez [Création de tests codés de l’interface utilisateur](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate) et [Anatomie d’un test codé de l’interface utilisateur](../test/anatomy-of-a-coded-ui-test.md).  
  
 Le code généré pour le mappage d'IU contient une classe pour chaque objet avec lequel le test interagit. Pour chaque méthode générée, une classe compagnon pour les paramètres de méthode est générée spécifiquement pour cette méthode. S'il existe un grand nombre d'objets, de pages, de formulaires et de contrôles dans votre application, le mappage d'IU peut devenir très grand. De plus, si plusieurs personnes travaillent sur des tests, l'application devient complexe avec un seul fichier de mappage d'IU de grande taille.  
  
 L'utilisation de plusieurs fichiers de mappages d'IU peut offrir les avantages suivants :  
  
-   Chaque mappage peut être associé à un sous-ensemble logique de l'application. Cela facilite la gestion des modifications.  
  
-   Chaque testeur peut travailler sur une section de l'application et archiver son code sans interférer avec le travail des autres testeurs sur d'autre sections de l'application.  
  
-   Les ajouts à l'interface utilisateur de l'application peuvent être mis à l'échelle de manière incrémentielle avec un impact minimal sur les tests exécutés sur d'autres parties de l'interface utilisateur.  
  
## <a name="do-you-need-multiple-ui-maps"></a>Avez-vous besoin de plusieurs mappages d'IU ?  
 Créez plusieurs mappages d'IU dans chacun des types de situations suivants :  
  
-   Plusieurs jeux complexes de contrôles d'IU composites qui, ensemble, effectuent une opération logique, par exemple une page d'inscription dans un site web ou la page d'achat d'un panier.  
  
-   Un jeu indépendant de contrôles accessibles à partir de différents points de l'application, par exemple un Assistant avec plusieurs pages d'opérations. Si chaque page de l'Assistant est particulièrement complexe, vous pourriez créer des mappages d'IU distincts pour chaque page.  
  
## <a name="adding-multiple-ui-maps"></a>Ajout de plusieurs mappages d'IU  
  
#### <a name="to-add-a-ui-map-to-your-coded-ui-test-project"></a>Pour ajouter un mappage d'IU à votre projet de test codé de l'interface utilisateur  
  
1.  Dans l’**Explorateur de solutions**, pour créer un dossier dans votre projet de test codé de l’interface utilisateur où stocker tous les mappages d’IU, cliquez avec le bouton droit sur le fichier de projet de test codé de l’interface utilisateur, pointez sur **Ajouter**, puis choisissez **Nouveau dossier**. Par exemple, vous pourriez le nommer `UIMaps`.  
  
     Le nouveau dossier apparaît sous le projet de test codé de l’interface utilisateur.  
  
2.  Cliquez avec le bouton droit sur le dossier `UIMaps`, pointez sur **Ajouter**, puis choisissez **Nouvel élément**.  
  
     La boîte de dialogue **Ajouter un nouvel élément** s’affiche.  
  
    > [!NOTE]
    >  Vous devez être dans un projet de test codé de l'interface utilisateur pour ajouter un nouveau mappage de test codé de l'interface utilisateur.  
  
3.  Sélectionnez **Mappage de test codé de l’interface utilisateur** dans la liste.  
  
     Dans la zone **Nom**, entrez le nom du nouveau mappage d’IU. Utilisez le nom du composant ou de la page que représentera le mappage, par exemple `HomePageMap`.  
  
4.  Sélectionnez **Ajouter**.  
  
     La fenêtre [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] est réduite et la boîte de dialogue **Générateur de test codé de l’interface utilisateur** s’affiche.  
  
5.  Enregistrez les actions de la première méthode et choisissez **Générer le code**.  
  
6.  Après avoir enregistré toutes les actions et assertions pour le premier composant ou la première page et les avoir regroupées dans des méthodes, fermez la boîte de dialogue **Générateur de test codé de l’interface utilisateur**.  
  
7.  Continuez à créer des mappages d'IU. Enregistrez les actions et assertions, regroupez-les dans des méthodes pour chaque composant, puis générez le code.  
  
 Dans de nombreux cas, la fenêtre de niveau supérieur de votre application reste constante pour tous les Assistants, formulaires et pages. Bien que chaque mappage d'IU ait une classe pour la fenêtre de niveau supérieur, tous les mappages font probablement référence à la même fenêtre de niveau supérieur dans laquelle tous les composants de l'application s'exécutent. Les tests codés de l'interface utilisateur recherchent les contrôles de manière hiérarchique, de haut en bas, en commençant par la fenêtre de niveau supérieur. Ainsi, dans une application complexe, la fenêtre de niveau supérieur réelle pourrait être dupliquée dans chaque mappage d'IU. Si la fenêtre de niveau supérieur réelle est dupliquée, plusieurs modifications ont lieu si cette fenêtre change. Cela pourrait provoquer des problèmes de performances quand vous basculez d'un mappage d'IU à un autre.  
  
 Pour limiter ce risque, vous pouvez utiliser la méthode `CopyFrom()` pour vous assurer que la nouvelle fenêtre de niveau supérieur dans ce mappage d'IU est identique à la fenêtre de niveau supérieur principale.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant fait partie d'une classe utilitaire qui fournit l'accès à chaque composant et à ses composants enfants représentés par les classes générées dans les différents mappages d'IU.  
  
 Dans cet exemple, une application web nommée `Contoso` possède une page d'accueil, une page de produits et une page de panier. Chacune de ces pages partage une fenêtre de niveau supérieur commune qui est la fenêtre du navigateur. Il existe un mappage d'IU pour chaque page et le code de la classe utilitaire est semblable au suivant :  
  
```  
using ContosoProject.UIMaps;  
using ContosoProject.UIMaps.HomePageClasses;  
using ContosoProject.UIMaps.ProductPageClasses;  
using ContosoProject.UIMaps.ShoppingCartClasses;  
  
namespace ContosoProject  
{  
    public class TestRunUtility  
    {  
        // Private fields for the properties  
        private HomePage homePage = null;  
        private ProductPage productPage = null;  
        private ShoppingCart shoppingCart = null;  
  
        public TestRunUtility()  
        {  
            homePage = new HomePage();  
        }  
  
        // Properties that get each UI Map  
        public HomePage HomePage  
        {  
            get { return homePage; }  
            set { homePage = value; }  
        }  
  
        // Gets the ProductPage from the ProductPageMap.  
        public ProductPage ProductPageObject  
        {  
            get  
            {  
                if (productPage == null)  
                {  
                    // Instantiate a new page from the UI Map classes  
                    productPage = new ProductPage();  
  
                    // Since the Product Page and Home Page both use  
                    // the same browser page as the top level window,  
                    // get the top level window properties from the  
                    // Home Page.  
                    productPage.UIContosoFinalizeWindow.CopyFrom(  
                        HomePage.UIContosoWindowsIWindow);  
                }  
                return productPage;  
            }  
        }  
  
    // Continue to create properties for each page, getting the   
    // page object from the corresponding UI Map and copying the   
    // top level window properties from the Home Page.  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.BrowserWindow.CopyFrom%2A>   
 [Utiliser UI Automation pour tester votre code](../test/use-ui-automation-to-test-your-code.md)   
 [Création de tests codés de l’interface utilisateur](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Anatomie d’un test codé de l’interface utilisateur](../test/anatomy-of-a-coded-ui-test.md)
