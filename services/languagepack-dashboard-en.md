<style>
    .dashboard-container h1,.dashboard-container h2,.dashboard-container h3,.dashboard-container h4,.dashboard-container h5,.dashboard-container p {
    color: #353A40;
}
.dashboard-container h1 {
    font-weight: 400;
    font-size: 32px !important;
    margin-top: 0;
}
.dashboard-container h2 {
    font-weight: 400;
    font-size: 24px;
}
.dashboard-container h3 {
    font-weight: 400;
    font-size: 20px;
}
.dashboard-container h4 {
    font-weight: 400;
    font-size: 16px;
}
.dashboard-container h5 {
    font-weight: 400;
    font-size: 13px;
    letter-spacing: 0px;
}
.dashboard-container p {
    font-weight: 400;
    font-size: 13px;
}
.service-component {
    max-width: 580px;    
}
</style>

# Language packs

Language packs are not executable services, but collections of message templates and forms.

Some services, like Staffing, Messaging, and Incident, have a language setting. For this setting to work, you also need to have the associated language pack installed, which is why these services automatically start installing a service pack after they have been installed.

The included message templates, forms, and form paths are all installed using a separate workflow containing all resources. These can be changed, but note that they will be reset to default texts when an update of the language pack is installed.

You can have multiple language packs installed, but only one can be active at a time. Any activities using a specific language setting will continue to use resources from this language pack even if the setting is changed. If you want to switch the language pack, please also start a new activity.
