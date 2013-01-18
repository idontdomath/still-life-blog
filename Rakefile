def jekyll(opts="", path="")
  sh "rm -rf _site"
  sh path + "jekyll " + opts
end

desc "Build site using Jekyll"
task :build do
  jekyll
end

desc "Serve on Localhost with port 4000"
task :default do
  jekyll "--server --auto"
end

desc "Serve on Localhost with port 4000 using development version"
task :unstable do
  jekyll "--server --auto", "../jekyll/bin/"
end

namespace :deploy do

  desc "Deploy to Live"
  task :live => :build do
    rsync "still.idontdomath.com.ar"
  end
  
  def rsync(domain)
    sh "rsync -rtz --delete _site/ iamak@idontdomath.com.ar:~/#{domain}/"
  end
end
