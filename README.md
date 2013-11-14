Unity.Mvc5
==========

Unity.Mvc5 is a library that allows simple Integration of Microsoft's Unity IoC container with ASP.NET MVC 5.

It is an update of the popular Unity.Mvc3 package, updated to target .NET 4.5, MVC5 and Unity 3.0.


Getting started with Unity.Mvc5
-------------------------------

The easiest way to add Unity.Mvc5 to your project is via the NuGet package. You can search for unity.mvc5 using the GUI or type the following into the package manager console in Visual Studio:

> install-package Unity.Mvc5

Once installed, just add a call to UnityConfig.RegisterComponents() in the Application_Start method of Global.asax.cs 
and the MVC framework will then use the Unity.Mvc5 DependencyResolver to resolve your components.

e.g.
 
    public class MvcApplication : System.Web.HttpApplication
    {
      protected void Application_Start()
      {
        AreaRegistration.RegisterAllAreas();
        UnityConfig.RegisterComponents();                           // <----- Add this line
        FilterConfig.RegisterGlobalFilters(GlobalFilters.Filters);
        RouteConfig.RegisterRoutes(RouteTable.Routes);
        BundleConfig.RegisterBundles(BundleTable.Bundles);
      }           
    }  

Add your Unity registrations in the RegisterComponents method of the UnityConfig class. All components that implement IDisposable should be 
registered with the HierarchicalLifetimeManager to ensure that they are properly disposed at the end of the request.

More Information
----------------

You can find out more about what has changed in this release by visiting the <a href="http://blog.feedbackhound.com/taking-ownership-of-unity.mvc-and-unity.webapi">FeedbackHound Blog</a>.
