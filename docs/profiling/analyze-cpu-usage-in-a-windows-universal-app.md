---
title: "Analyser l&#39;utilisation de l&#39;UC dans les applications du Windows Store | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: c122b08e-e3bf-43e6-bd6c-e776e178fd9a
caps.latest.revision: 16
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
robots: noindex,nofollow
---
# Analyser l&#39;utilisation de l&#39;UC dans les applications du Windows Store
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

![S'applique à Windows et Windows Phone](../debugger/media/windows_and_phone_content.png "windows\_and\_phone\_content")  
  
 Quand vous devez examiner les problèmes de performances de votre application, il est utile de commencer par comprendre comment elle utilise le processeur.  L'outil **Utilisation de l'UC** du hub Performances et diagnostics de Visual Studio vous indique l'endroit où le processeur consacre du temps à exécuter le code C\+\+, C\#\/VB et JavaScript.  Pour examiner des scénarios spécifiques, l'outil Utilisation de l'UC peut être exécuté avec l'outil [Réactivité de l'interface utilisateur XAML](../Topic/Analyze%20UI%20responsiveness%20in%20Store%20apps%20\(XAML\).md), l'outil [Consommation d'énergie](../profiling/analyze-energy-use-in-store-apps.md), ou les deux, dans une seule session de diagnostic.  L'outil Utilisation de l'UC remplace l'outil Échantillonnage de l'UC de Visual Studio 2013.  
  
> [!NOTE]
>  L'outil **Utilisation de l'UC** ne peut pas être utilisé avec les applications Silverlight Windows Phone 8.1.  
  
 Cette procédure pas à pas vous guide pour la collecte et l'analyse de l'utilisation du processeur pour une application simple.  
  
 Vous utiliserez les procédures par défaut du [hub Performances et diagnostics](../Topic/Run%20analysis%20tools%20from%20the%20Performance%20and%20Diagnostic%20page.md) pour collecter les données, mais ce dernier vous offre bien d'autres options pour exécuter et gérer votre session de diagnostic.  Par exemple, vous pouvez exécuter l'outil Utilisation de l'UC sur des applications Windows Phone ou Windows Store, exécuter la session de diagnostic sur l'ordinateur Visual Studio, sur un appareil Windows Phone ou Windows Store, ou dans l'un des émulateurs ou simulateurs Visual Studio.  
  
 Vous examinerez ensuite en détail le rapport diagnostique d'utilisation de l'UC.  
  
## Sommaire  
 [Créer le projet CpuUseDemo](#BKMK_Create_the_CpuUseDemo_project)  
  
 [Qu'est-ce que CpuUseDemo ?](#BKMK_What_is_CpuUseDemo_)  
  
 [Collecter les données d'utilisation de l'UC](#BKMK_Collect_CPU_usage_data)  
  
 [Analyser le rapport d'utilisation de l'UC](#BKMK_Analyze_the_CPU_Usage_report)  
  
 [Étapes suivantes](#BKMK_Next_steps)  
  
 [MainPage.xaml](#BKMK_MainPage_xaml)  
  
 [MainPage.xaml.cs](#BKMK_MainPage_xaml_cs)  
  
##  <a name="BKMK_Create_the_CpuUseDemo_project"></a> Créer le projet CpuUseDemo  
  
1.  Créez un projet d'application Windows Store en C\# nommé **CpuUseDemo** à l'aide du modèle **BlankApp**.  
  
2.  Remplacez MainPage.xaml par [ce code](#BKMK_MainPage_xaml).  
  
3.  Remplacez MainPage.xaml.cs par [ce code](#BKMK_MainPage_xaml_cs).  
  
##  <a name="BKMK_What_is_CpuUseDemo_"></a> Qu'est\-ce que CpuUseDemo ?  
 **CpuUseDemo** est une application qui a été créée pour expliquer comment collecter et analyser les données d'utilisation de l'UC.  Les boutons génèrent un nombre en appelant une méthode qui sélectionne la valeur maximale de plusieurs appels à une fonction.  La fonction appelée crée un très grand nombre de valeurs aléatoires, puis retourne la dernière.  Les données sont affichées dans une zone de texte.  Générez l'application et essayez\-la.  
  
 L'application n'est pas très attractive et les méthodes de CpuUseDemo ne sont pas très intéressantes, mais elle est suffisamment simple pour vous montrer certains cas courants d'analyse des données d'utilisation de l'UC.  
  
##  <a name="BKMK_Collect_CPU_usage_data"></a> Collecter les données d'utilisation de l'UC  
  
1.  Dans Visual Studio, définissez la cible de déploiement sur **Simulateur** et la configuration de la solution sur **Commercial**.  
  
    -   L'exécution de l'application dans le simulateur vous permet de passer facilement de l'application à l'interface IDE de Visual Studio.  
  
    -   L'exécution de cette application en mode **Release** vous donne un meilleur aperçu des performances réelles de votre application.  
  
2.  Dans le menu **Déboguer**, sélectionnez **Performances et diagnostics**.  
  
3.  Dans le hub Performances et diagnostics, choisissez **Utilisation de l'UC**, puis **Démarrer**.  
  
4.  Quand l'application démarre, cliquez sur **Obtenir le nombre maximal**.  Attendez environ une seconde après l'affichage de la sortie, puis choisissez **Obtenir le nombre maximal asynchrone**.  Le temps de pause entre les clics de bouton permet d'isoler plus facilement les routines de clic de bouton dans le rapport diagnostique.  
  
5.  Quand apparaît la deuxième ligne de sortie, choisissez **Arrêter la collecte** dans le hub Performances et diagnostics.  
  
 L'outil Utilisation de l'UC analyse les données et affiche le rapport.  
  
##  <a name="BKMK_Analyze_the_CPU_Usage_report"></a> Analyser le rapport d'utilisation de l'UC  
 [Graphique chronologique d'utilisation de l'UC](#BKMK_CPU_utilization_timeline_graph) **&#124;** [Sélectionner des segments chronologiques pour afficher les détails](#BKMK_Select_timeline_segments_to_view_details) **&#124;** [Arborescence des appels de l'outil Utilisation de l'UC](#BKMK_The_CPU_Usage_call_tree) **&#124;** [Structure de l'arborescence des appels](#BKMK_Call_tree_structure) **&#124;** [Code externe](#BKMK_External_Code) **&#124;** [Colonnes des données de l'arborescence des appels](#BKMK_Call_tree_data_columns) **&#124;** [Fonctions asynchrones de l'arborescence des appels d'Utilisation de l'UC](#BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree)  
  
###  <a name="BKMK_CPU_utilization_timeline_graph"></a> Graphique chronologique d'utilisation de l'UC  
 Le graphique d'utilisation de l'UC indique l'activité processeur de l'application sous forme de pourcentage du temps processeur total de tous les processeurs de l'appareil.  Les données de ce rapport ont été collectées sur une machine double cœur.  Les deux grandes pointes représentent l'activité processeur de deux clics de bouton.  `GetMaxNumberButton_Click` s'effectue de manière synchrone sur un seul cœur, il est donc normal que la hauteur du graphique de la méthode ne dépasse jamais 50 %.  `GetMaxNumberAsycButton_Click` s'exécute de manière asynchrone sur les deux cœurs, il est donc également normal que sa pointe soit presqu'aussi élevée qu'en cas d'utilisation de toutes les ressources processeur sur les deux cœurs.  
  
####  <a name="BKMK_Select_timeline_segments_to_view_details"></a> Sélectionner des segments chronologiques pour afficher les détails  
 Utilisez les barres de sélection de la chronologie de la **Session de diagnostic** pour vous concentrer sur les données de GetMaxNumberButton\_Click :  
  
 La chronologie de la **Session de diagnostic** affiche désormais le temps écoulé dans le segment sélectionné \(un peu plus de 2 secondes dans ce rapport\) et filtre l'arborescence des appels à ces méthodes qui ont exécuté la sélection.  
  
 Sélectionnez maintenant le segment `GetMaxNumberAsyncButton_Click`.  
  
 Cette méthode se termine environ une seconde plus rapidement que `GetMaxNumberButton_Click`, mais la signification des entrées de l'arborescence des appels est moins évidente.  
  
###  <a name="BKMK_The_CPU_Usage_call_tree"></a> Arborescence des appels de l'outil Utilisation de l'UC  
 Pour bien comprendre les informations de l'arborescence des appels, resélectionnez le segment `GetMaxNumberButton_Click` et observez les détails de l'arborescence des appels.  
  
####  <a name="BKMK_Call_tree_structure"></a> Structure de l'arborescence des appels  
  
|||  
|-|-|  
|![Étape 1](../profiling/media/procguid_1.png "ProcGuid\_1")|Le nœud de premier niveau des arborescences d'appels de l'outil Utilisation de l'UC est un pseudo\-nœud|  
|![Étape 2](../profiling/media/procguid_2.png "ProcGuid\_2")|Dans la plupart des applications, quand l'option **Afficher le code externe** est désactivée, le nœud de deuxième niveau est un nœud **\[Code externe\]** contenant le code système et de l'infrastructure qui démarre et arrête l'application, dessine l'interface utilisateur, contrôle la planification des threads et fournit d'autres services de niveau inférieur à l'application.|  
|![Étape 3](../profiling/media/procguid_3.png "ProcGuid\_3")|Les enfants du nœud de deuxième niveau sont les méthodes en code utilisateur et des routines asynchrones appelées ou créées par le code système et d'infrastructure de deuxième niveau.|  
|![Étape 4](../profiling/media/procguid_4.png "ProcGuid\_4")|Les nœuds enfants d'une méthode contiennent des données seulement pour les appels de la méthode parente.  Quand **Afficher le code externe** est désactivé, les méthodes d'application contiennent également un nœud **\[Code externe\]**.|  
  
####  <a name="BKMK_External_Code"></a> Code externe  
 Le code externe représente des fonctions des composants système et de l'infrastructure exécutés par le code que vous écrivez.  Le code externe comprend notamment des fonctions qui démarrent et arrêtent l'application, dessinent l'interface utilisateur, contrôlent les threads et fournissent d'autres services de deuxième niveau à l'application.  Dans la plupart des cas, vous ne vous intéressez pas au code externe et l'arborescence des appels de l'outil Utilisation de l'UC rassemble les fonctions externes d'une méthode utilisateur en un nœud **\[Code externe\]**.  
  
 Quand vous voulez afficher les chemins d'appel du code externe, choisissez **Afficher le code externe** dans la liste **Filtrer la vue**, puis **Appliquer**.  
  
 N'oubliez pas que de nombreuses chaînes d'appel en code externe sont profondément imbriquées, la largeur de la colonne Nom de fonction ne peut pas dépasser la largeur d'affichage de presque tous les moniteurs d'ordinateur, sauf les plus larges.  Si tel est le cas, les noms de fonction sont affichés sous forme de **\[…\]** :  
  
 Utilisez la zone de recherche pour trouver le nœud que vous cherchez, puis utilisez la barre de défilement horizontal pour afficher les données dans la vue :  
  
###  <a name="BKMK_Call_tree_data_columns"></a> Colonnes des données de l'arborescence des appels  
  
|||  
|-|-|  
|**Processeur total \(%\)**|Pourcentage de l'activité processeur de l'application dans la période de temps sélectionnée qui a été utilisée par les appels à la fonction et les fonctions appelées par la fonction.  Notez la différence avec le graphique chronologique d'**Utilisation de l'UC**, qui compare l'activité totale de l'application dans une période de temps à la capacité totale disponible du processeur.|  
|**Processeur auto \(%\)**|Pourcentage de l'activité processeur de l'application dans la période de temps sélectionnée qui a été utilisé par les appels à la fonction, sans compter l'activité des fonctions appelées par la fonction.|  
|**Processeur total \(ms\)**|Nombre de millisecondes écoulées en appels à la fonction dans la période de temps sélectionnée et les fonctions qui ont été appelées par la fonction.|  
|**Processeur auto \(ms\)**|Nombre de millisecondes écoulées en appels à la fonction dans la période de temps sélectionnée et les fonctions qui ont été appelées par la fonction.|  
|**Module**|Nom du module contenant la fonction ou nombre de modules contenant les fonctions dans un nœud \[Code externe\].|  
  
###  <a name="BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree"></a> Fonctions asynchrones de l'arborescence des appels d'Utilisation de l'UC  
 Quand le compilateur rencontre une méthode asynchrone, il crée une classe masquée pour contrôler l'exécution de la méthode.  Dans son concept, la classe est une machine d'état comprenant une liste des fonctions générées par le compilateur qui appellent de manière asynchrone des opérations de la méthode d'origine, et les rappels, le planificateur et les itérateurs qui leur sont nécessaires.  Quand la méthode d'origine est appelée par une méthode parente, le runtime supprime la méthode du contexte d'exécution du parent et exécute les méthodes de la classe masquée dans le contexte du code système et de l'infrastructure qui contrôle l'exécution de l'application.  Les méthodes asynchrones sont souvent, mais pas toujours, exécutées sur un ou plusieurs threads différents.  Ce code est indiqué dans l'arborescence des appels d'Utilisation de l'UC en tant qu'enfants du nœud **\[Code externe\]** immédiatement en dessous du premier nœud de l'arborescence.  
  
 Pour le voir dans notre exemple, resélectionnez le segment `GetMaxNumberAsyncButton_Click` dans la chronologie.  
  
 Les deux premiers nœuds sous **\[Code externe\]** sont les méthodes générées par le compilateur de la classe de la machine d'état.  Le troisième est l'appel à la méthode d'origine.  En développant les méthodes générées, vous avez un aperçu de ce qui se passe.  
  
-   `MainPage::GetMaxNumberAsyncButton_Click` a une action très réduite : elle gère une liste de valeurs de tâche, calcule le maximum des résultats et affiche la sortie.  
  
-   `MainPage+<GetMaxNumberAsyncButton_Click>d__3::MoveNext` vous indique l'activité requise pour planifier et lancer les 48 tâches qui constituent l'appel à `GetNumberAsync`.  
  
-   `MainPage::<GetNumberAsync>b__b` vous montre l'activité des tâches appelant `GetNumber`.  
  
##  <a name="BKMK_Next_steps"></a> Étapes suivantes  
 L'application CpuUseDemo n'est pas la plus sensationnelle des applications, mais vous pouvez étendre son utilité en l'utilisant pour la tester avec le fonctionnement asynchrone et d'autres outils du hub Performances et diagnostics.  
  
-   Notez que `MainPage::<GetNumberAsync>b__b` consacre plus de temps au \[Code externe\] qu'à l'exécution de la méthode GetNumber.  Une grande partie de ce temps est consacré au traitement des opérations asynchrones.  Essayez d'augmenter le nombre de tâches \(défini dans la constante `NUM_TASKS` de MainPage.xaml.cs\) et de réduire le nombre d'itérations dans `GetNumber` \(modifiez la valeur `MIN_ITERATIONS`\).  Exécutez le scénario de collecte et comparez l'activité processeur de `MainPage::<GetNumberAsync>b__b` à celle de la session de diagnostic d'Utilisation de l'UC d'origine.  Essayez de réduire les tâches et d'augmenter les itérations.  
  
-   Souvent, les utilisateurs ne s'intéressent pas aux performances réelles de votre application, mais aux performances perçues et à la réactivité de l'application.  L'outil Réactivité de l'interface utilisateur XAML vous montre les détails de l'activité sur le thread d'interface utilisateur qui affecte la perception de la réactivité.  
  
     Créez une session dans le hub Performances et diagnostics et ajoutez les outils Réactivité de l'interface utilisateur XAML et Utilisation de l'UC.  Exécutez le scénario de collecte.  À ce stade, le rapport ne vous dit probablement rien que vous ne sachiez déjà, mais les différences entre les graphiques chronologiques d'**Utilisation du thread d'interface utilisateur** des deux méthodes sont frappantes.  Dans les applications complexes du monde réel, la combinaison des outils peut être très utile.  
  
##  <a name="BKMK_MainPage_xaml"></a> MainPage.xaml  
  
```c#  
<Page  
    x:Class="CpuUseDemo.MainPage"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:local="using:CpuUseDemo"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    mc:Ignorable="d">  
  
    <Page.Resources>  
        <Style TargetType="TextBox">  
            <Setter Property="FontFamily"  Value="Lucida Console" />  
        </Style>  
    </Page.Resources>  
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">  
        <Grid.RowDefinitions>  
            <RowDefinition Height="Auto" />  
            <RowDefinition Height="*" />  
        </Grid.RowDefinitions>  
        <StackPanel Grid.Row="0" Orientation="Horizontal"  Margin="0,40,0,0">  
            <Button Name="GetMaxNumberButton" Click="GetMaxNumberButton_Click"  Content="Get Max Number" />  
            <Button Name="GetMaxNumberAsyncButton" Click="GetMaxNumberAsyncButton_Click"  Content="Get Max Number Async" />  
        </StackPanel>  
        <StackPanel Grid.Row="1">  
            <TextBox Name="TextBox1" AcceptsReturn="True" />  
        </StackPanel>  
    </Grid>  
  
</Page>  
  
```  
  
##  <a name="BKMK_MainPage_xaml_cs"></a> MainPage.xaml.cs  
  
```c#  
using System;  
using System.Collections.Generic;  
using System.IO;  
using System.Linq;  
using System.Runtime.InteropServices.WindowsRuntime;  
using Windows.Foundation;  
using Windows.Foundation.Collections;  
using Windows.UI.Xaml;  
using Windows.UI.Xaml.Controls;  
using Windows.UI.Xaml.Controls.Primitives;  
using Windows.UI.Xaml.Data;  
using Windows.UI.Xaml.Input;  
using Windows.UI.Xaml.Media;  
using Windows.UI.Xaml.Navigation;  
using Windows.Foundation.Diagnostics;  
using System.Threading;  
using System.Threading.Tasks;  
using System.Collections.Concurrent;  
  
// The Blank Page item template is documented at http://go.microsoft.com/fwlink/?LinkId=234238  
  
namespace CpuUseDemo  
{  
    /// <summary>  
    /// An empty page that can be used on its own or navigated to within a Frame.  
    /// </summary>  
    public sealed partial class MainPage : Page  
    {  
        public MainPage()  
        {  
            this.InitializeComponent();  
        }  
  
        const int NUM_TASKS = 48;  
        const int MIN_ITERATIONS = int.MaxValue / 1000;  
        const int MAX_ITERATIONS = MIN_ITERATIONS + 10000;  
  
        long m_totalIterations = 0;  
        readonly object m_totalItersLock = new object();  
  
        private void GetMaxNumberButton_Click(object sender, RoutedEventArgs e)  
        {  
            GetMaxNumberAsyncButton.IsEnabled = false;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations = 0;  
            }  
            List<int> tasks = new List<int>();  
            for (var i = 0; i < NUM_TASKS; i++)  
            {  
                var result = 0;  
                result = GetNumber();  
                tasks.Add(result);  
            }  
            var max = tasks.Max();  
            var s = GetOutputString("GetMaxNumberButton_Click", NUM_TASKS, max, m_totalIterations);  
            TextBox1.Text += s;  
            GetMaxNumberAsyncButton.IsEnabled = true;  
        }  
  
        private async void GetMaxNumberAsyncButton_Click(object sender, RoutedEventArgs e)  
        {  
            GetMaxNumberButton.IsEnabled = false;  
            GetMaxNumberAsyncButton.IsEnabled = false;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations = 0;  
            }  
            var tasks = new ConcurrentBag<Task<int>>();  
            for (var i = 0; i < NUM_TASKS; i++)  
            {  
                tasks.Add(GetNumberAsync());  
            }  
            await Task.WhenAll(tasks.ToArray());  
            var max = 0;  
            foreach (var task in tasks)  
            {  
                max = Math.Max(max, task.Result);  
            }  
            var func = "GetMaxNumberAsyncButton_Click";  
            var outputText = GetOutputString(func, NUM_TASKS, max, m_totalIterations);  
            TextBox1.Text += outputText;  
            this.GetMaxNumberButton.IsEnabled = true;  
            GetMaxNumberAsyncButton.IsEnabled = true;  
        }  
  
        private int GetNumber()  
        {  
            var rand = new Random();  
            var iters = rand.Next(MIN_ITERATIONS, MAX_ITERATIONS);  
            var result = 0;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations += iters;  
            }  
            // we're just spinning here  
            // and using Random to frustrate compiler optimizations  
            for (var i = 0; i < iters; i++)  
            {  
                result = rand.Next();  
            }  
            return result;  
        }  
  
        private Task<int> GetNumberAsync()  
        {  
            return Task<int>.Run(() =>  
            {  
                return GetNumber();  
            });  
        }  
  
        string GetOutputString(string func, int cycles, int max, long totalIters)  
        {  
            var fmt = "{0,-35}Tasks:{1,3}    Maximum:{2, 12}    Iterations:{3,12}\n";  
            return String.Format(fmt, func, cycles, max, totalIters);  
        }  
  
    }  
}  
  
```