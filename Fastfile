# This file contains the fastlane.tools configuration
# You can find the documentation at https://docs.fastlane.tools
#
# For a list of all available actions, check out
#
#     https://docs.fastlane.tools/actions
#
# For a list of all available plugins, check out
#
#     https://docs.fastlane.tools/plugins/available-plugins
#

# Uncomment the line if you want fastlane to automatically update itself
# update_fastlane

default_platform(:ios)

def prepare_version(options)
    increment_version_number(
        version_number: options[:version]
    )

    increment_build_number(
        build_number: options[:build]
    )
end


platform :ios do

  build = get_build_number()

  # 时间戳
  currentTimeStamp = `date '+%s'`
  base_output_directory = "/Users/omega/Desktop/auto"
  product_name = "A01"

  ipa_name = "#{build}_#{currentTimeStamp}AA"
  workspace_name = ""

  desc "打包项目测试"

  before_all do
    	cocoapods(
  		clean: true,
  		podfile: "./Podfile"
   	)
  end


  lane :custom_lane do
     
    
    # add actions here: https://docs.fastlane.tools/actions
    # 构建和打包ipa
     gym(scheme: "FastlaneTest",
          	output_directory: "./build/a",
            configuration: "Release",  # 配置为Release版本
          	workspace: "FastlaneTest.xcworkspace",
            output_name: ipa_name,
            include_bitcode: true)
  end


  lane :custom_local do
     
    
     
    # add actions here: https://docs.fastlane.tools/actions

    output_directory = "#{base_output_directory}/#{product_name}/iOS/local"
    # 构建和打包ipa
     gym(scheme: "FastlaneTest",
            output_directory: output_directory,
            configuration: "Debug",  # 配置为Release版本
            workspace: "FastlaneTest.xcworkspace",
            output_name: ipa_name,
            include_bitcode: true)
  end

  lane :custom_test do
     
    
    # add actions here: https://docs.fastlane.tools/actions
    # 构建和打包ipa
     gym(scheme: "FastlaneTest",
            output_directory: "/Users/omega/Desktop/auto/A01/iOS/test",
            configuration: "Debug",  # 配置为Debug版本
            workspace: "FastlaneTest.xcworkspace",
            output_name: ipa_name,
            include_bitcode: true)
  end

  lane :custom_online do
     
    
    # add actions here: https://docs.fastlane.tools/actions
    # 构建和打包ipa
     gym(scheme: "FastlaneTest",
            output_directory: "/Users/omega/Desktop/auto/A01/iOS/online",
            configuration: "Release",  # 配置为Release版本
            workspace: "FastlaneTest.xcworkspace",
            output_name: ipa_name,
            include_bitcode: true)
  end

  after_all do |lane|

  end

  error do |lane, exception|
    # slack(
    #   message: "Error message"
    # )
  end
end
