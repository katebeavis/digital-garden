# No bundle url present

`No bundle url present. Make sure you’re running a packager server or have included a .jsbundle file in your application bundle.`

`$ react-native run-ios`

Packager server runs on port 8081

`$ lsof -i :8081`

If nothing is runnong on port 8081 this meeans that you need to run the Metro bundler

`npx react-native start`
