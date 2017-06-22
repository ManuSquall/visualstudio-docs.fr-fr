---
title: Utilisation de shims pour isoler votre application des autres assemblys pour des tests unitaires| Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d2a34de2-6527-4c21-8b93-2f268ee894b7
caps.latest.revision: 12
ms.author: douge
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 1d64aafdb107e0398c25f6efed7203524c111f18
ms.contentlocale: fr-fr
ms.lasthandoff: 05/13/2017

---
# <a name="using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing"></a>Utilisation de shims pour isoler votre application des autres assemblys pour des tests unitaires
Les **types shim** sont l’une des deux technologies utilisées par le framework Microsoft Fakes pour vous permettre d’isoler facilement des composants testés de l’environnement. Les shims détournent les appels à des méthodes spécifiques vers le code que vous écrivez dans le cadre de votre test. De nombreuses méthodes retournent des résultats différents selon les conditions externes, mais un shim est sous le contrôle de votre test et peut retourner des résultats cohérents lors de chaque appel. Cela facilite l'écriture de vos tests.  
  
 Utilisez les shims pour isoler le code des assemblys qui ne font pas partie de votre solution. Pour isoler les composants de votre solution les uns des autres, nous vous recommandons d'utiliser les stubs.  
  
 Pour obtenir une vue d’ensemble et un guide de démarrage rapide, consultez [Isolation du code sous test avec Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md).  
  
 **Requirements**  
  
-   Visual Studio Enterprise  
  
 Consultez la [vidéo (1h16) : Testing Un-testable Code with Fakes in Visual Studio 2012](http://go.microsoft.com/fwlink/?LinkId=261837).  
  
## <a name="in-this-topic"></a>Dans cette rubrique  
 Voici ce que vous allez apprendre dans cette rubrique :  
  
 [Exemple : le bogue de l’an 2000](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Example__The_Y2K_bug)  
  
 [Procédure d’utilisation des shims](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Fakes_requirements)  
  
-   [Ajouter les assemblys Fakes](#AddFakes)  
  
-   [Utiliser ShimsContext](#ShimsContext)  
  
-   [Écrire des tests avec des shims](#WriteTests)  
  
 [Shims pour différents types de méthodes](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Shim_basics)  
  
-   [Méthodes statiques](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Static_methods)  
  
-   [Méthodes d’instance (pour toutes les instances)](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Instance_methods__for_all_instances_)  
  
-   [Méthodes d’instance (pour une instance de runtime)](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Instance_methods__for_one_instance_)  
  
-   [Constructeurs](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Constructors)  
  
-   [Membres de base](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Base_members)  
  
-   [Constructeurs statiques](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Static_constructors)  
  
-   [Finaliseurs](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Finalizers)  
  
-   [Méthodes privées](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Private_methods)  
  
-   [Interfaces de liaison](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Binding_interfaces)  
  
 [Modification du comportement par défaut](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Changing_the_default_behavior)  
  
 [Détection des accès à l’environnement](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Detecting_environment_accesses)  
  
 [Concurrence](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Concurrency)  
  
 [Appel de la méthode d’origine à partir de la méthode shim](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Calling_the_original_method_from_the_shim_method)  
  
 [Limitations](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Limitations)  
  
##  <a name="BKMK_Example__The_Y2K_bug"></a>Exemple : le bogue de l’an 2000  
 Prenons l’exemple d’une méthode qui lève une exception le 1er janvier 2000 :  
  
```c#  
// code under test  
public static class Y2KChecker {  
    public static void Check() {  
        if (DateTime.Now == new DateTime(2000, 1, 1))  
            throw new ApplicationException("y2kbug!");  
    }  
}  
  
```  
  
 Le test de cette méthode est particulièrement problématique, car le programme dépend de `DateTime.Now`, une méthode qui dépend de l'horloge de l'ordinateur, une méthode dépendante de l'environnement et non déterministe. En outre, `DateTime.Now` étant une propriété statique, un type stub ne peut pas être utilisé ici. Ce problème est le symptôme du problème d'isolation dans les tests unitaires : les programmes qui appellent directement les API de base de données communiquent avec les services web et il est donc difficile de procéder à des tests unitaires, car leur logique dépend de l'environnement.  
  
 C'est dans ce cas que les types shim doivent être utilisés. Les types shim fournissent un mécanisme pour détourner toute méthode .NET vers un délégué défini par l'utilisateur. Les types shim sont générés par le code par le générateur Fakes et utilisent des délégués, que nous appelons types shim, pour spécifier les nouvelles implémentations des méthodes.  
  
 Le test suivant montre comment utiliser le type shim, `ShimDateTime`, pour fournir une implémentation personnalisée de DateTime.Now :  
  
```c#  
//unit test code  
// create a ShimsContext cleans up shims   
using (ShimsContext.Create()  
    // hook delegate to the shim method to redirect DateTime.Now  
    // to return January 1st of 2000  
    ShimDateTime.NowGet = () => new DateTime(2000, 1, 1);  
    Y2KChecker.Check();  
}  
  
```  
  
##  <a name="BKMK_Fakes_requirements"></a> Procédure d’utilisation des shims  
  
###  <a name="AddFakes"></a> Ajouter les assemblys Fakes  
  
1.  Dans l’Explorateur de solutions, développez les **Références** de votre projet de test unitaire.  
  
    -   Si vous utilisez Visual Basic, vous devez sélectionner **Afficher tous les fichiers** dans la barre d’outils de l’Explorateur de solutions pour afficher la liste de références.  
  
2.  Sélectionnez l'assembly contenant les définitions de classes pour lesquelles vous souhaitez créer des shims. Par exemple, si vous souhaitez effectuer un shim pour DateTime, sélectionnez System.dll  
  
3.  Dans le menu contextuel, choisissez **Ajouter un assembly Fakes**.  
  
###  <a name="ShimsContext"></a> Utiliser ShimsContext  
 Lors de l'utilisation de types shim dans un framework de tests unitaires, vous devez encapsuler le code de test dans un `ShimsContext` pour contrôler la durée de vie de vos shims. Sans cette exigence, les shims dureraient jusqu’à l’arrêt d’AppDomain. La façon la plus facile de créer un `ShimsContext` consiste à utiliser la méthode statique `Create()` comme illustré dans le code suivant :   
  
```c#  
//unit test code  
[Test]  
public void Y2kCheckerTest() {  
  using(ShimsContext.Create()) {  
    ...  
  } // clear all shims  
}  
  
```  
  
 Il est essentiel de supprimer correctement chaque contexte de shim. En règle générale, appelez toujours `ShimsContext.Create` à l'intérieur d'une instruction `using` pour garantir le nettoyage correct des shims inscrits. Par exemple, vous pouvez inscrire un shim pour une méthode de test qui remplace la méthode `DateTime.Now` par un délégué qui retourne toujours le premier janvier 2000. Si vous oubliez d'effacer le shim inscrit dans la méthode de test, le reste de la série de tests retourne toujours le premier janvier 2000 comme valeur DateTime.Now. Cela peut être surprenant et déroutant.  
  
###  <a name="WriteShims"></a> Écrire un test avec les shims  
 Dans votre code de test, insérez un *détour* pour la méthode que vous souhaitez falsifier. Exemple :  
  
```c#  
[TestClass]  
public class TestClass1  
{   
        [TestMethod]  
        public void TestCurrentYear()  
        {  
            int fixedYear = 2000;  
  
            using (ShimsContext.Create())  
            {  
              // Arrange:  
                // Detour DateTime.Now to return a fixed date:  
                System.Fakes.ShimDateTime.NowGet =   
                () =>  
                { return new DateTime(fixedYear, 1, 1); };  
  
                // Instantiate the component under test:  
                var componentUnderTest = new MyComponent();  
  
              // Act:  
                int year = componentUnderTest.GetTheCurrentYear();  
  
              // Assert:   
                // This will always be true if the component is working:  
                Assert.AreEqual(fixedYear, year);  
            }  
        }  
}  
  
```  
  
```vb#  
<TestClass()> _  
Public Class TestClass1  
    <TestMethod()> _  
    Public Sub TestCurrentYear()  
        Using s = Microsoft.QualityTools.Testing.Fakes.ShimsContext.Create()  
            Dim fixedYear As Integer = 2000  
            ' Arrange:  
            ' Detour DateTime.Now to return a fixed date:  
            System.Fakes.ShimDateTime.NowGet = _  
                Function() As DateTime  
                    Return New DateTime(fixedYear, 1, 1)  
                End Function  
  
            ' Instantiate the component under test:  
            Dim componentUnderTest = New MyComponent()  
            ' Act:  
            Dim year As Integer = componentUnderTest.GetTheCurrentYear  
            ' Assert:   
            ' This will always be true if the component is working:  
            Assert.AreEqual(fixedYear, year)  
        End Using  
    End Sub  
End Class  
```  
  
 Les noms de classe de shim sont obtenus en ajoutant le préfixe `Fakes.Shim` au nom de type d'origine.  
  
 Les shims fonctionnent en insérant des *détours* dans le code de l’application testée. Lors de chaque appel à la méthode d'origine, le système Fakes effectue un détour : au lieu d'appeler la véritable méthode, le code de votre shim est appelé.  
  
 Notez que les détours sont créés et supprimés au moment de l'exécution. Vous devez toujours créer un détour dans la durée de vie de `ShimsContext`. Lorsqu'il est supprimé, tous les shims créés quand il était actif sont supprimés. La meilleure façon de procéder est à l'intérieur d'une instruction `using`.  
  
 Vous pouvez voir une erreur de génération indiquant que l'espace de noms Fakes n'existe pas. Cette erreur apparaît parfois lorsqu'il existe d'autres erreurs de compilation. Corrigez les autres erreurs et elle disparaîtra.  
  
##  <a name="BKMK_Shim_basics"></a> Shims pour différents types de méthodes  
 Les types shim vous permettent de remplacer toute méthode .NET, y compris les méthodes statiques ou méthodes non virtuelles, par vos propres délégués.  
  
###  <a name="BKMK_Static_methods"></a> Méthodes statiques  
 Les propriétés permettant d'attacher des shims à des méthodes statiques sont placées dans un type shim. Chaque propriété possède uniquement un accesseur Set qui peut être utilisé pour attacher un délégué à la méthode cible. Par exemple, prenons une classe `MyClass` avec une méthode statique `MyMethod` :  
  
```c#  
//code under test  
public static class MyClass {  
    public static int MyMethod() {  
        ...  
    }  
}  
```  
  
 Nous pouvons attacher un shim à `MyMethod` qui retourne toujours 5 :  
  
```c#  
// unit test code  
ShimMyClass.MyMethod = () =>5;  
```  
  
###  <a name="BKMK_Instance_methods__for_all_instances_"></a> Méthodes d’instance (pour toutes les instances)  
 Comme les méthodes statiques, les méthodes d'instance peuvent faire l'objet d'un shim pour toutes les instances. Les propriétés permettant d'attacher ces shims sont placées dans un type imbriqué nommé AllInstances pour éviter toute confusion. Par exemple, prenons une classe `MyClass` avec une méthode d'instance `MyMethod` :  
  
```c#  
// code under test  
public class MyClass {  
    public int MyMethod() {  
        ...  
    }  
}  
```  
  
 Vous pouvez attacher un shim à `MyMethod` qui retourne toujours 5, quelle que soit l'instance :  
  
```c#  
// unit test code  
ShimMyClass.AllInstances.MyMethod = () => 5;  
```  
  
 La structure du type généré de ShimMyClass ressemble au code suivant :  
  
```c#  
// Fakes generated code  
public class ShimMyClass : ShimBase<MyClass> {  
    public static class AllInstances {  
        public static Func<MyClass, int>MyMethod {  
            set {  
                ...  
            }  
        }  
    }  
}  
```  
  
 Notez que Fakes passe l’instance de runtime comme premier argument du délégué dans ce cas.  
  
###  <a name="BKMK_Instance_methods__for_one_instance_"></a> Méthodes d’instance (pour une instance de runtime)  
 Les méthodes d'instance peuvent également faire l'objet d'un shim par des délégués différents, selon le destinataire de l'appel. Cela permet à la même méthode d'instance d'avoir des comportements différents par instance du type. Les propriétés permettant de configurer ces shims sont des méthodes d'instance du type shim lui-même. Chaque type shim instancié est également associé à une instance brute d'un type ayant fait l'objet d'un shim.  
  
 Par exemple, prenons une classe `MyClass` avec une méthode d'instance `MyMethod` :  
  
```c#  
// code under test  
public class MyClass {  
    public int MyMethod() {  
        ...  
    }  
}  
```  
  
 Nous pouvons configurer deux types shim de MyMethod de façon à ce que le premier retourne toujours 5 et le deuxième retourne toujours 10 :  
  
```c#  
// unit test code  
var myClass1 = new ShimMyClass()  
{  
    MyMethod = () => 5  
};  
var myClass2 = new ShimMyClass { MyMethod = () => 10 };  
```  
  
 La structure du type généré de ShimMyClass ressemble au code suivant :  
  
```c#  
// Fakes generated code  
public class ShimMyClass : ShimBase<MyClass> {  
    public Func<int> MyMethod {  
        set {  
            ...  
        }  
    }  
    public MyClass Instance {  
        get {  
            ...  
        }  
    }  
}  
```  
  
 L'instance du type ayant fait l'objet d'un shim véritable est accessible via la propriété Instance :  
  
```c#  
// unit test code  
var shim = new ShimMyClass();  
var instance = shim.Instance;  
```  
  
 Comme le type shim a également une conversion implicite vers le type ayant fait l'objet d'un shim, vous pouvez généralement utiliser tout simplement le type shim tel quel :  
  
```c#  
// unit test code  
var shim = new ShimMyClass();  
MyClass instance = shim; // implicit cast retrieves the runtime  
                         // instance  
```  
  
###  <a name="BKMK_Constructors"></a> Constructeurs  
 Les constructeurs peuvent également faire l'objet d'un shim pour attacher les types shim aux futurs objets. Chaque constructeur est exposé comme un constructeur de méthode statique dans le type shim. Par exemple, prenons une classe `MyClass` avec un constructeur qui prend un entier :  
  
```c#  
// code under test  
public class MyClass {  
    public MyClass(int value) {  
        this.Value = value;  
    }  
    ...  
}  
```  
  
 Nous définissons le type shim du constructeur afin que chaque instance ultérieure retourne -5 quand l'accesseur Get Value est appelé, indépendamment de la valeur dans le constructeur :  
  
```c#  
// unit test code  
ShimMyClass.ConstructorInt32 = (@this, value) => {  
    var shim = new ShimMyClass(@this) {  
        ValueGet = () => -5  
    };  
};  
```  
  
 Notez que chaque type shim expose deux constructeurs. Le constructeur par défaut doit être utilisé quand une nouvelle instance est nécessaire, tandis que le constructeur prenant une instance ayant fait l'objet d'un shim comme argument doit être utilisé dans les shims constructeurs uniquement :   
  
```c#  
// unit test code  
public ShimMyClass() { }  
public ShimMyClass(MyClass instance) : base(instance) { }  
```  
  
 La structure du type généré de ShimMyClass ressemble au code suivant :  
  
```c#  
// Fakes generated code  
public class ShimMyClass : ShimBase<MyClass>  
{  
    public static Action<MyClass, int> ConstructorInt32 {  
        set {  
            ...  
        }  
    }  
  
    public ShimMyClass() { }  
    public ShimMyClass(MyClass instance) : base(instance) { }  
    ...  
}  
```  
  
###  <a name="BKMK_Base_members"></a> Membres de base  
 Les propriétés du shim des membres de base sont accessibles en créant un shim pour le type de base et en passant l'instance enfant comme paramètre au constructeur de la classe de base du shim.  
  
 Par exemple, prenons une classe `MyBase` avec une méthode d'instance `MyMethod` et un sous-type `MyChild` :  
  
```c#  
public abstract class MyBase {  
    public int MyMethod() {  
        ...  
    }  
}  
  
public class MyChild : MyBase {  
}  
  
```  
  
 Nous pouvons configurer un shim de `MyBase` en créant un shim `ShimMyBase` :  
  
```c#  
// unit test code  
var child = new ShimMyChild();  
new ShimMyBase(child) { MyMethod = () => 5 };  
```  
  
 Notez que le type shim enfant est implicitement converti en instance enfant quand il est passé comme paramètre au constructeur de shim de base.  
  
 La structure du type généré de ShimMyChild et ShimMyBase ressemble au code suivant :  
  
```c#  
// Fakes generated code  
public class ShimMyChild : ShimBase<MyChild> {  
    public ShimMyChild() { }  
    public ShimMyChild(Child child)  
        : base(child) { }  
}  
public class ShimMyBase : ShimBase<MyBase> {  
    public ShimMyBase(Base target) { }  
    public Func<int> MyMethod  
    { set { ... } }  
}  
```  
  
###  <a name="BKMK_Static_constructors"></a> Constructeurs statiques  
 Les types shim exposent une méthode statique `StaticConstructor` pour effectuer un shim sur le constructeur statique d'un type. Étant donné que les constructeurs statiques sont exécutés une fois seulement, vous devez vous assurer que le shim est configuré avant d’accéder à n’importe quel membre du type.  
  
###  <a name="BKMK_Finalizers"></a> Finaliseurs  
 Les finaliseurs ne sont pas pris en charge dans Fakes.  
  
###  <a name="BKMK_Private_methods"></a> Méthodes privées  
 Le générateur de code Fakes crée des propriétés de shim pour les méthodes privées qui ont uniquement des types visibles dans la signature, autrement dit des types de paramètres et un type de retour visibles.  
  
###  <a name="BKMK_Binding_interfaces"></a> Interfaces de liaison  
 Quand un type ayant fait l'objet d'un shim implémente une interface, le générateur de code émet une méthode qui lui permet de lier tous les membres de cette interface à la fois.  
  
 Par exemple, prenons une classe `MyClass` qui implémente `IEnumerable<int>` :  
  
```c#  
public class MyClass : IEnumerable<int> {  
    public IEnumerator<int> GetEnumerator() {  
        ...  
    }  
    ...  
}  
  
```  
  
 Nous pouvons effectuer un shim sur les implémentations d'`IEnumerable<int>` dans MyClass en appelant la méthode Bind :  
  
```c#  
// unit test code  
var shimMyClass = new ShimMyClass();  
shimMyClass.Bind(new List<int> { 1, 2, 3 });  
  
```  
  
 La structure du type généré de ShimMyClass ressemble au code suivant :  
  
```c#  
// Fakes generated code  
public class ShimMyClass : ShimBase<MyClass> {  
    public ShimMyClass Bind(IEnumerable<int> target) {  
        ...  
    }  
}  
  
```  
  
##  <a name="BKMK_Changing_the_default_behavior"></a> Modification du comportement par défaut  
 Chaque type shim généré contient une instance de l'interface `IShimBehavior`, via la propriété `ShimBase<T>.InstanceBehavior`. Le comportement est utilisé chaque fois qu'un client appelle un membre d'instance qui n'a pas fait l'objet d'un shim de façon explicite.  
  
 Si le comportement n'a pas été défini explicitement, il utilise l'instance retournée par la propriété statique `ShimsBehaviors.Current`. Par défaut, cette propriété retourne un comportement qui lève une exception `NotImplementedException`.  
  
 Ce comportement peut être modifié à tout moment en définissant la propriété `InstanceBehavior` sur toute instance de shim. Par exemple, l'extrait de code suivant remplace le shim par un comportement qui ne fait rien ou retourne la valeur par défaut du type de retour, autrement dit default(T) :  
  
```c#  
// unit test code  
var shim = new ShimMyClass();  
//return default(T) or do nothing  
shim.InstanceBehavior = ShimsBehaviors.DefaultValue;  
  
```  
  
 Le comportement peut également être modifié globalement pour toutes les instances ayant fait l'objet d'un shim pour lesquelles la propriété `InstanceBehavior` n'a pas été définie explicitement en définissant la propriété statique `ShimsBehaviors.Current` :  
  
```c#  
// unit test code  
// change default shim for all shim instances  
// where the behavior has not been set  
ShimsBehaviors.Current =   
    ShimsBehaviors.DefaultValue;  
  
```  
  
##  <a name="BKMK_Detecting_environment_accesses"></a> Détection des accès à l’environnement  
 Il est possible d'associer un comportement à tous les membres, y compris les méthodes statiques, d'un type particulier en assignant le comportement `ShimsBehaviors.NotImplemented` à la propriété statique `Behavior` du type shim correspondant :  
  
```c#  
// unit test code  
// assigning the not implemented behavior  
ShimMyClass.Behavior = ShimsBehaviors.NotImplemented;  
// shorthand  
ShimMyClass.BehaveAsNotImplemented();  
  
```  
  
##  <a name="BKMK_Concurrency"></a> Accès concurrentiel  
 Les types shim s’appliquent à tous les threads de l’AppDomain et n’ont pas d’affinité de thread. Il s'agit d'un fait important si vous prévoyez d'utiliser un Test Runner qui prend en charge la concurrence : les tests impliquant des types shim ne peuvent pas s'exécuter simultanément. Cette propriété n'est pas appliquée par le runtime Fakes.  
  
##  <a name="BKMK_Calling_the_original_method_from_the_shim_method"></a> Appel de la méthode d’origine à partir de la méthode shim  
 Supposons que nous voulons réellement écrire le texte vers le système de fichiers après avoir validé le nom du fichier passé à la méthode. Dans ce cas, nous voulons appeler la méthode d'origine au milieu de la méthode shim.  
  
 La première approche pour résoudre ce problème consiste à encapsuler un appel à la méthode d'origine en utilisant un délégué et `ShimsContext.ExecuteWithoutShims()` comme dans le code suivant :  
  
```c#  
// unit test code  
ShimFile.WriteAllTextStringString = (fileName, content) => {  
  ShimsContext.ExecuteWithoutShims(() => {  
  
      Console.WriteLine("enter");  
      File.WriteAllText(fileName, content);  
      Console.WriteLine("leave");  
  });  
};  
  
```  
  
 Une autre approche consiste à affecter au shim la valeur null, à appeler la méthode d'origine et à restaurer le shim.  
  
```c#  
// unit test code  
ShimsDelegates.Action<string, string> shim = null;  
shim = (fileName, content) => {  
  try {  
    Console.WriteLine("enter");  
    // remove shim in order to call original method  
    ShimFile.WriteAllTextStringString = null;  
    File.WriteAllText(fileName, content);  
  }  
  finally  
  {  
    // restore shim  
    ShimFile.WriteAllTextStringString = shim;  
    Console.WriteLine("leave");  
  }  
};  
// initialize the shim  
ShimFile.WriteAllTextStringString = shim;  
  
```  
  
##  <a name="BKMK_Limitations"></a> Limitations  
 Les shims ne peuvent pas être utilisés sur tous les types à partir de la bibliothèque de classes de base .NET **mscorlib** et **System**.  
  
## <a name="external-resources"></a>Ressources externes  
  
### <a name="guidance"></a>Conseils  
 [Test de la livraison continue avec Visual Studio 2012 - Chapitre 2 : Tests unitaires : tester l’intérieur](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
## <a name="see-also"></a>Voir aussi  
 [Isolation du code sous test avec Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)   
 [Blog de Peter Provost : shims Visual Studio 2012](http://www.peterprovost.org/blog/2012/04/25/visual-studio-11-fakes-part-2)   
 [Vidéo (1h16) : Testing Un-testable Code with Fakes in Visual Studio 2012](http://go.microsoft.com/fwlink/?LinkId=261837)

