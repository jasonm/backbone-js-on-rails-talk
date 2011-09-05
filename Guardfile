require 'guard/guard'

module ::Guard
  class Landslide < Guard
    def start
      UI.info "landslide is waiting for slide changes..."
    end

    def run_all
      true
    end

    def run_on_change(paths)
      UI.info "landslide is generating a new presentation..."
      output = `landslide landslide.cfg`

      command_failure = ($?.to_i != 0)

      if command_failure
        UI.error output

        UI.error "*"*80
        UI.error "Errors in generation listed above!"
        UI.error "*"*80
      else
        UI.info "Done."
      end
    end
  end
end

guard 'landslide' do
  watch (%r{landslide\.cfg|slides/})
end
